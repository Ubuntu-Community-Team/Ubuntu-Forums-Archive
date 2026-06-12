---
title: "Change Ubuntu 16.04 splash screen"
date: 2017-01-29
forum: Desktop Environments
---

### Post by stevetingate on 2017-01-29
HI i am running ubuntu desktop 16.04 and want to change the spalash screen to a .mp4 i have
can anyone help me ?

i read that i need to use plymouth but cant find any info on install and how to change it ?

---

### Post by Dennis N on 2017-01-29
Your goal may be unattainable. I think you need an image file with a fixed image (probably of a limited type), as there is a script that controls all the components of the splash screen - it may require .png as a background but not sure on that.

Added information:

In 16.04 and later, look at /usr/share/plymouth/themes/ for the theme folders. In Ubuntu, it is probably "ubuntu-logo". Inside the theme folder are probably some images, and a script, probably ubuntu-logo.script that controls the action. One image is probably the wallpaper used for the splash. It should be obvious if you use thumbnail view on the folder. I woulds rename that image from the original name, then substitute a wallpaper of the same type and size but use the original name.

Caveat: Did not test this for you (I don't have Ubuntu 16.04 in use), but seems low risk and easy to undo if desired.

Contents of Xubuntu-logo theme folder in Xubuntu:

```
dmn@Sydney:/usr/share/plymouth/themes/xubuntu-logo$ ls
fsck-fade_16bit.png  progress-fade_16bit.png   test.png
fsck-fade.png        progress-fade.png         [COLOR="#0000FF"]wallpaper.png[/COLOR]
logo_16bit.png       progress-meter_16bit.png  xubuntu-logo.plymouth
logo.png             progress-meter.png        xubuntu-logo.script
passw-dialog.png     spinner.png
```

---

### Post by gdesilva on 2017-01-29
As Dennis N mentioned playing mp4 is not possible as Plymouth is only an interim display till the proper graphics drivers a fully loaded. The best you can do is to either simply change the background as mentioned above, install a new Plymouth script or write your own plymouth script.

---

