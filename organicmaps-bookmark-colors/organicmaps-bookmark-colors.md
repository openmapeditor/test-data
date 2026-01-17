# Organic Maps Bookmark Colors

Reference for the 16 predefined bookmark colors used in [Organic Maps](https://omaps.app/).

| Color Name     | KML (AABBGGRR) | CSS (#RRGGBB) | Icon URL                                              |
| :------------- | :------------- | :------------ | :---------------------------------------------------- |
| **Red**        | `FF231BE5`     | `#E51B23`     | https://omaps.app/placemarks/placemark-red.png        |
| **Pink**       | `FF8241FF`     | `#FF4182`     | https://omaps.app/placemarks/placemark-pink.png       |
| **Purple**     | `FFB2249B`     | `#9B24B2`     | https://omaps.app/placemarks/placemark-purple.png     |
| **DeepPurple** | `FFBF3966`     | `#6639BF`     | https://omaps.app/placemarks/placemark-deeppurple.png |
| **Blue**       | `FFCC6600`     | `#0066CC`     | https://omaps.app/placemarks/placemark-blue.png       |
| **LightBlue**  | `FFF29C24`     | `#249CF2`     | https://omaps.app/placemarks/placemark-lightblue.png  |
| **Cyan**       | `FFCDBE14`     | `#14BECD`     | https://omaps.app/placemarks/placemark-cyan.png       |
| **Teal**       | `FF8CA500`     | `#00A58C`     | https://omaps.app/placemarks/placemark-teal.png       |
| **Green**      | `FF3C8C3C`     | `#3C8C3C`     | https://omaps.app/placemarks/placemark-green.png      |
| **Lime**       | `FF39BF93`     | `#93BF39`     | https://omaps.app/placemarks/placemark-lime.png       |
| **Yellow**     | `FF00C8FF`     | `#FFC800`     | https://omaps.app/placemarks/placemark-yellow.png     |
| **Orange**     | `FF0096FF`     | `#FF9600`     | https://omaps.app/placemarks/placemark-orange.png     |
| **DeepOrange** | `FF3264F0`     | `#F06432`     | https://omaps.app/placemarks/placemark-deeporange.png |
| **Brown**      | `FF334680`     | `#804633`     | https://omaps.app/placemarks/placemark-brown.png      |
| **Gray**       | `FF737373`     | `#737373`     | https://omaps.app/placemarks/placemark-gray.png       |
| **BlueGray**   | `FF807359`     | `#597380`     | https://omaps.app/placemarks/placemark-bluegray.png   |

## Development Reference

### KML Encoding Logic

Organic Maps uses the `AABBGGRR` (Alpha-Blue-Green-Red) format for **Lines**. For **Points**, the color is determined by the **Icon URL** rather than a hex code.

To convert a standard CSS `#RRGGBB` hex color for a track:

1. Prepend `FF` (for full opacity).
2. Swap the Red and Blue components.

**Formula:** `FF` + `BB` + `GG` + `RR`

### JavaScript Implementation

This is the function used in OpenMapEditor to perform the conversion:

```javascript
/**
 * Converts a CSS hex color to KML AABBGGRR format.
 * @param {string} cssColor - CSS color string (e.g., "#E51B23")
 * @returns {string} KML color string (e.g., "FF231BE5")
 */
function cssToKmlColor(cssColor) {
  const rr = cssColor.substring(1, 3);
  const gg = cssColor.substring(3, 5);
  const bb = cssColor.substring(5, 7);
  return `FF${bb}${gg}${rr}`.toUpperCase();
}
```
