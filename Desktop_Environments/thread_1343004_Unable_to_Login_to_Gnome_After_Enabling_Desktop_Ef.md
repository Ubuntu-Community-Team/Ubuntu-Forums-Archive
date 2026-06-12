---
title: "Unable to Login to Gnome After Enabling Desktop Effects (Compiz)"
date: 2009-12-01
forum: Desktop Environments
---

### Post by JefferyHunt on 2009-12-01
After I upgraded to Karmic I decided to give Compiz a spin and see if it worked now, why not right? previously in 9.04 I would turn effects on and an error message would tell me that they couldn't be enabled. Whatever, no big deal. On 9.10, however, instead of giving me an error message, I was sent to the login screen. Now trying to login to Gnome only sends me back to the login screen again and again. After entering my credentials It looks like its loggin in then the screen goes blank, then like magic we're back to the login screen. I can login to xterm and and run gconf, I removed both Current and Default USR/BIN/COMPIZ. After that I get the same problem. Then from the terminal I ran gnome-appearance-properties and made sure that the effects were set to "none" which they now were and for good measure I ran metacity --replace. After exiting the xterm session and trying to loggin to Gnome I am still faced with the same problem. How do I fix it?

---

### Post by trytenn on 2009-12-01
I'm not sure it's a good idea to remove the bin/compiz manually. Try uninstalling it with apt instead. But u may be missing some libraries so it could be a better idea to install ubuntu-desktop with recommends (including compiz-libraries). Have u checked if u have any broken packages? sudo apt-get check. Try that first and install missing packages. 
But if it is some settings that is wrong, there is a way to delete all settings. Then ubuntu creates default settings-files. I had to do that ones but it's not a good way.

---

### Post by JefferyHunt on 2009-12-01
Thanks I tried your suggestions. There weren't any packages that needed to be fixed. However I did discover something weird. Whenever I turn on my computer and try logging into Gnome I still have my problem. However, when I boot into recovery mode and fix the "Grub bootloader" (Whatever that means) then reboot from there I am able to login normally. However if I restart and try logging in again I can't unless I go through this process every time. I've tested this about five times. so weird. Anyway there are many people that use this computer who know nothing about linux and would be really freaked out if they had to try something like that everytime they wanted to check facebook. Any ideas what my problem is. I'm novice but have been around linux long enough to follow any instructions one might have.

---

### Post by trytenn on 2009-12-01
I don't know if I can help you. But have you tried both with and without full compiz installation?
Compiz changed my settings too some time ago, and I couldn't figure out how to change them back so i deleted the gconf settings files. It's almost like getting a fresh install of ubuntu but without loosing any programs and files. Anyway, it's an ugly solution and someone out there may have a better one.

---

