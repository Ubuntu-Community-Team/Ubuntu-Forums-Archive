---
title: "View as Icons"
date: 2016-07-31
forum: Desktop Environments
---

### Post by zkab on 2016-07-31
I have Ubuntu desktop (Xfce) 16.04 LTS and Thunar 1.6.10
When I select 'View as Icons' in Thunar then some jpg-images are shown as a generic icons (black filled squares with text JPG in white letters)
What should be done to preview all images in icon-view-mode ?

---

### Post by ajgreeny on 2016-07-31
Try renaming the hidden folder .thumbnails in your home as a backup with command ```
mv .thumbnails .thumbnails-backup
```
Maybe there is something corrupt in that folder.

---

### Post by zkab on 2016-08-01
Didn't work

---

### Post by ajgreeny on 2016-08-01
In many file-managers there is a more detailed configuration for previews, ie, thumbnails of image files, but other than turning them on or off and "Local files only/Never/Always", I can not really find much more for thunar's behaviour.

It will be interesting to see if anyone else has any idea if this is more controllable.

---

### Post by zkab on 2016-08-06
Anyone ?

---

