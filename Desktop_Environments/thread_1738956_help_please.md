---
title: "help please?"
date: 2011-04-25
forum: Desktop Environments
---

### Post by Gabriel Washington on 2011-04-25
When I first installed kubuntu 11.04 beta 2 (64-bit) all desktop effects were working fine until I updated kubuntu. After that every time I try to enable desktop effects it will temporarily do it for at least 10 seconds then say that desktop effects were to slow and were suspended, I really don't know what is the cause of this.
 Im a linux noob,.

---

### Post by 3Miro on 2011-04-25
What is your video card? If it is Nvidia, you can try to reinstall the nvidia driver. Go to menu -> search for Additional Drivers. Form there:

1. Deactivate any Nvidia drivers.
2. Reboot.
3. Reactivate the Nvidia driver.
4. Reboot.

Note that if you are a noob, then you probably shouldn't be messing with pre-release beta versions. It will make your life easier.

---

### Post by Gabriel Washington on 2011-04-25
I don't have a nividia video card it's intel

---

### Post by 3Miro on 2011-04-25
I have had bad experience with KDE and Intel in general. KDE effects seems quite GPU intensive (especially if you are using an external monitor), or this may be a bug that will be resolved soon. Try playing with the effects settings and lower the GPU requirements and/or disable some of the effects. The advanced tab in the Desktop Effects in System Settings has quite a few options.

---

### Post by el_koraco on 2011-04-26
Try this. open the Home folder, click ALT and . and find the .kde folder. Rename it to .kde_backup or something. This will reset your KDE values to the default. If necessary, reboot. Let's see what happens then. You'll have to make all you customizations again. 

It might be a bug with KWin and some post beta2 updates, I've had the same problem as you and managed to sort it out using the described method. Renaming the .kde folder in Home will leave it there in case you need to use it again.

---

