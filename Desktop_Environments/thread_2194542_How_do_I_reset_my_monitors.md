---
title: "How do I reset my monitors?"
date: 2013-12-19
forum: Desktop Environments
---

### Post by timswait on 2013-12-19
I use a laptop (Dell M2000) with Kubuntu. I have a monitor which I plug into the VGA output and normally use, it's all been fine for ages. I recently seem to have upset it by opening the lid on the laptop and plugging the monitor in at the same time. This made it cycle through a strange combination of displaying garbled rubbish on both the laptop screen and the monitor. When I uplugged the monitor the laptop went back to displaying correctly on it's own screen. However now whenever I plug the monitor in both screens go blank (the monitor displays "no signal"). When I unplug the monitor my laptop screen comes back on. When I boot up the computer with the monitor connected I get the kubuntu logo on both screens and the login as normal, the splash screen also displays correctly on both screens, but when it gets to load the desktop then both screens go blank. Again unplugging the monitor makes the laptop one work again.
Is there an easy way I can go back to default settings for the screens and get it to autodetect the screens from scratch? In the past I thought I could remove xorg.conf from the etc/x11 folder to force it to make a new one, but I don't see an xorg.conf file in my x11 folder, so I guess this has changed with new versions of kubuntu?

---

### Post by timswait on 2013-12-19
I've now just made the problem much worse! I had the idea that if I renamed the .kde directory in my home directory then that would force it to create a new one the next time I logged on and would reset everything to default (not ideal but I'd run out of other ideas). So I renamed it to .oldkde thinking I could always rename it back to .kde if it didn't work. It didn't work, I can't log in at all now. And even worse I forgot that my home folder was encrypted so now I can't rename it back again! Can someone please tell me how to access my home folder and change the name of folder .oldkde back to .kde. I can access the guest account or boot to live CD or to recovery mode.
Cheers.

---

### Post by timswait on 2013-12-19
Just fixed the most recent problem:). Changed the .kde folder back to its original name using the instructions here for mounting my encrypted home folder: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory)
However I'm still left with the original problem of how to reset my display settings back to defaults. Surely it can't be this hard :( There must be configuration file somewhere and if I could just find it and delete it or modify it to force it to reconnect to the VGA monitor as though it hadn't seen it before....

---

### Post by timswait on 2014-01-06
I have now fixed this. Upgraded to 13.10 hoping that would solve it, but it didn't. However, now when I re-named the .kde folder to .old_kde, it automatically created a new .kde folder which contained all default settings. Rebooting then made it start up with everything kde set to default, so the monitor now works! Admittedly I've had to change all my other settings back to the way I like them, but that's a small price to pay. So if you are running 13.10 an easy way to reset all kde settings is to delete or rename your .kde folder and it'll create a new default one. However don't try this if you're running an older version as it won't!

---

