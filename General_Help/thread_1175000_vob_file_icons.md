---
title: "vob file icons"
date: 2009-05-31
forum: General Help
---

### Post by Ceiber Boy on 2009-05-31
i have a number of vob files on my desktop, some of the generic icons (the film reel). have been replaced by images from the video, but others have remained as the generic icon.

i have played all the files and have compared the properties boxes, all to no avail,

dose anyone have any idea or suggestions on why not all the icons have changed  please.

---

### Post by steeleyuk on 2009-05-31
It will have been because Totem failed to grab the shot from the film. This can happen for a number of reasons but it usually happens due to:

a) High CPU load, the grabbing fails to complete in time
b) The video is corrupt and it can't grab a shot

To regenerate the images, you need to open your home folder and press CTRL + H. Hidden folders will show. You then need to go into the .thumbnails folder and then into each of the three folders (fail, normal, large)... deleting the images inside.

Beware that this will mean that every thumbnail you've indexed before will need regenerating.

---

### Post by Ceiber Boy on 2009-05-31
> **steeleyuk said:**
> It will have been because Totem failed to grab the shot from the film. This can happen for a number of reasons but it usually happens due to:

a) High CPU load, the grabbing fails to complete in time
b) The video is corrupt and it can't grab a shot

To regenerate the images, you need to open your home folder and press CTRL + H. Hidden folders will show. You then need to go into the .thumbnails folder and then into each of the three folders (fail, normal, large)... deleting the images inside.

Beware that this will mean that every thumbnail you've indexed before will need regenerating.



thanks that worked, but how dose totem know what image to display out of all the frames?

---

