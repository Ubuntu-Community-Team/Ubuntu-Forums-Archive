---
title: "Is &quot;Rotate images physically&quot; lossless?"
date: 2008-03-08
forum: Desktop Environments
---

### Post by Endolith on 2008-03-08
When you import photos from a camera, it gives you the option to "Rotate images physically", to match the EXIF data.  Is this transformation lossless?

---

### Post by azhtar on 2008-03-09
I think it only moves pixels from point A to Point B and doesn't compress the image again, also it depends on your software and your settings.

---

### Post by tschaboo on 2008-06-12
> **Endolith said:**
> When you import photos from a camera, it gives you the option to "Rotate images physically", to match the EXIF data.  Is this transformation lossless?

gThumb Manual v2.9.0 (feisty) says:
> 
         If the Rotate images physically checkbox is selected,
         and the imported photo contains an Exif orientation tag, the image data
         **will be physically transformed (losslessly)** so that the viewed image
         looks the same as before but the orientation tag is reset to "top left".
         If this checkbox is not enabled, the image data and the orientation tag
         are both left unchanged. The image will be displayed identically by
         gthumb for both possibilities, but for maximum compatibility with other
         applications this checkbox should be enabled.

---

### Post by Endolith on 2008-06-12
> **tschaboo said:**
> gThumb Manual v2.9.0 (feisty) says:

Good.  :)

---

