---
title: "Problem with Canon PowerShot S30 camera"
date: 2006-03-12
forum: Desktop Environments
---

### Post by dierre on 2006-03-12
Hello...

I own a Canon PowerShot S30 camera, which has a USB connector. This camera does not export a filesystem, so, in order to download your pictures, you have to pass through libgphoto2.

With ubuntu 5.04, whenever I plug in the camera, a dialog appeared asking me whether I wanted to import my pictures; if I answered yes, then ```
gthumb --import-photos
``` was launched. Everything worked very smoothly.

Unfortunately ubuntu 5.10 does not have this behaviour anymore :-( . If I plug in the camera, nothing happens. I have to manually start gphoto2 or gthumb. How do I re-enable that? Asking me whether I wanted to import photos and launching the appropriate program was very nice.

Besides... is this change of behaviour a "feature" or a bug that needs to be reported?

Thank you!

---

### Post by quonsar on 2006-03-12
run the configuration editor (found in the system tools menu) and navigate to /desktop/gnome/volume_manager and check the box that says 'autophoto' then edit the 'autophoto_command' key value to 'gnome-volume-manager-gthumb %h'

---

### Post by dierre on 2006-03-14
Tried that (even if those keys were already set as you suggested), but nothing changed... please note that the camera does work, because importing photos with the gphoto2 CLI program works just fine...

Have you got any other advice, please? Thank you!

---

