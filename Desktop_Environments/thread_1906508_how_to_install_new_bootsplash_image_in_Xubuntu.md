---
title: "how to install new bootsplash image in Xubuntu?"
date: 2012-01-09
forum: Desktop Environments
---

### Post by subehsharma on 2012-01-09
I tried configuring it by installing 'Super Boot Manager' and it applies correctly without giving any error messages but when i reboot the router, i still see blank screen and not bootsplash. Please help.

---

### Post by subehsharma on 2012-01-09
bump....anyone??

---

### Post by BobMarleyy on 2012-01-09
You might want to go to settings manager -> session and startup -> splash. Try changing it from none to simple and configure it as you like, e.g. you can change the background image

---

### Post by subehsharma on 2012-01-10
Thanks BobMarleyy but splash that you're talking about is not the one that I'm referring to. Its the one which comes when your system has been booting..like a progress bar which comes in Ubuntu while its booting.

---

### Post by cottfcfan on 2012-01-10
If its the boot/grub screen that you mean, the file you need to edit is /etc/default/grub & add the line:
GRUB_BACKGROUND=/path/to/file
under the line:
GRUB_CMDLINE_LINUX=""
for example:
GRUB_BACKGROUND=/usr/share/xfce4/backdrops/xubuntu-greybird.png
then run:
```
sudo update-grub
```

---

### Post by GraeW on 2012-01-10
Thanks for posting that, cottfcfan.. I was actually thinking about trying this out too, now I know where to look/edit, too :)

---

