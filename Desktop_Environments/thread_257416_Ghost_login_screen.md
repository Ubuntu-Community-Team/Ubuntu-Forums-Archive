---
title: "Ghost login screen"
date: 2006-09-14
forum: Desktop Environments
---

### Post by bantamsilver on 2006-09-14
Have loaded Ubuntu on aging P111 Vectra with MGA 200 graphics.The logon screen shows ghost image.It would appear that the correct drivers are not being loaded.Any help would be appreciated.Thanks

---

### Post by Markkreuzz on 2006-09-14
hmmm... can you describe the image even more??? maybe your monitor resolution is not set properly.
you can try booting to recovery mode and after logging in try typing in
```
sudo dpkg-reconfigure xserver-xorg 
``` and it should give you a setup wizard for Xorg. also try using vesa...

---

### Post by bantamsilver on 2006-09-14
Hi
The display is tearing on the righthand side.There are two pointer images and two login box images.Once past the login screen everything is fine.I have tried the re-configure suggestion, but still no joy.It seems like it loads on  a standard set of drivers, which are possibly wrong refresh rate.Then switches to the correct ones in the window enviroment.The graphics card is a Matrox MGA 200 on board.If it was a M/S windows system I would have it fixed by now but I'm still learning the command and file structure on Linux.Will try a different graphics card and see if it fixes it.
Thanks for the advice.

---

### Post by Markkreuzz on 2006-09-15
You can check "etc/X11/xorg.conf"  and i suggest lowering your vertical sync and horizontal sync and also check the 600x400 800x600 modes. if there is anyone else here that has the same card, please feel free to join in.

---

### Post by bantamsilver on 2006-09-15
Markkreuzz
Took the re-configure option and selected the Vesa option and the logon screen problems are fixed.Can I assume that the correct MGA drivers are not being loaded.If so I will Investigate this avenue.Thanks again for the help

---

### Post by Markkreuzz on 2006-09-15
very welcome... Anyway i suggested the vesa drivers because i have experienced display problems in the past with ubuntu on my geforce 6100 way back in 5.04. Also having display trouble with my other PC that has Dapper 6.06.1. as i have noticed ubuntu has limited drivers to choose from when you reconfigure xorg, i tried using vector linux (based on slackware) and when i configure xorg it gives me TONS of selections for graphic cards and was able to select the correct one s3 trio DX. unfortunately installing bleeding edge appz in vector is a pain so im stuck with xubuntu. Hope you find further answers to your questions...

---

