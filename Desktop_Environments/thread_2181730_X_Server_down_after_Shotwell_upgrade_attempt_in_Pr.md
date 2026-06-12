---
title: "X Server down after Shotwell upgrade attempt in Precise"
date: 2013-10-18
forum: Desktop Environments
---

### Post by tehowe on 2013-10-18
Got a doozy of a problem... I attempted to upgrade Shotwell in Precise by adding the gstreamer developer PPA and the Yorba (Shotwell developer PPA) as detailed by them here: [http://blog.yorba.org/clinton/2013/03/shotwell-0-14-released.html](http://blog.yorba.org/clinton/2013/03/shotwell-0-14-released.html)   There was some nonsense around the gstreamer installation - to version 1.0.0 IIRC, which I didn't force install, but I did have to uninstall then reinstall before apt stopped holding it back.   This effort broke X on reboot, and I've just got the console to work with now. Which is all we need, right? I've attempted reconfiguring/reinstalling lightdm, but after checking the log it's just exiting because X doesn't return the ready signal. It also says that some process 2015 returned an error code of 127 about 9s into the log. Okay... I tried installing gdm as well, which was useless in retrospect, and now I can't even get the console with CTRL-ALT-F1. The system's booting to a blank black screen. So gdm is not booting, either! What do you think's the best approach to take? Or even generally in troubleshooting X? The logfiles for X are voluminous, I don't really know where to start. Thanks;

---

### Post by tehowe on 2013-10-20
I've pieced together a fix from various sources online ... these are the  different steps I took to get my X server back up and running. I think  the original problem was that by upgrading certain packages lightdm was  left unconfigured and unable to boot. Your situation may be different,  and only part of or none of these steps will be useful to you. But if X  isn't coming up for you, this covers some of the main things to check  anyways.

The first thing to do is get the console back. If you can use the CTRL-ALT-F1 console already, skip to step 2.

1. ***Remove gdm***  - Since installing gdm alongside lightdm actually froze my system, I  rebooted holding down Shift to bring up the grub menu. From this menu,  pick a recovery kernel, then pick root shell, and remove gdm then  reconfigure the system to load lightdm. 

```
apt-get purge gdm
dpkg-reconfigure lightdm

```

2. ***Boot into console**.*  - Reboot at this point eg; type ```
shutdown now
```, start the  computer again, then when the splash screen's revealed you can hit Esc  to see what the system is doing as it loads. My system stopped at a  (probably unrelated) message about 'stopping System V compatibility'.  But I was still able to press CTRL-ALT-F1 to bring up the tty1 shell to  login with my desktop username and password.

3. **Start up lightdm manually**  - From the console, you can probably enter ```
sudo service lightdm  start
``` to start up the login screen. Press CTRL-ALT-F7 to get back  to the previously frozen GUI screen and log in.

Note, I was  having problems with my Unity installation and figured I may as well rip  out the Catalyst video driver I was using to see if the system would  come up easier if I dropped back to the open source Radeon drivers. You  may want to try this too if you have an AMD GPU that you suspect, or  just skip ahead to step 4. 
(see uninstall section:  [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)  )

4. **Set lightdm to run automatically again**. -  You may want to check and see if the file ~/.Xauthority is owned by  root, and set its ownership back to your username, as described in here:   [http://askubuntu.com/questions/65852/cannot-login-to-my-user-account/241989#241989](http://askubuntu.com/questions/65852/cannot-login-to-my-user-account/241989#241989)

Next, edit /etc/X11/default-display-manager as described here: [http://askubuntu.com/questions/74551/lightdm-not-starting-on-boot](http://askubuntu.com/questions/74551/lightdm-not-starting-on-boot)

Reboot,  and your system should bring up the login screen again, finally.  But  here's a couple bonus links for things I needed to do to get Unity and  my Radeon working again, since.
No panels/dock in Unity
[http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)
Reinstall Catalyst 
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

