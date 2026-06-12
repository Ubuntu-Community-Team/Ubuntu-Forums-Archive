---
title: "Changing the login screen"
date: 2017-03-23
forum: Desktop Environments
---

### Post by sven0 on 2017-03-23
I found this old thread about changing the login screen: [https://ubuntuforums.org/showthread.php?t=1871801](https://ubuntuforums.org/showthread.php?t=1871801)
but none of the solutions there worked for me when trying them with Lubuntu 17.04 beta-1.

After probing around a little, I changed the "[FONT=courier new]background=[/FONT]" line in the "[FONT=courier new][greeter][/FONT]" section in the file [FONT=courier new]/etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf[/FONT]
and that did the trick!

here are some keywords:

change wallpaper 
change login screen
lubuntu 17.04 
lightdm gtk theme greeter

---

