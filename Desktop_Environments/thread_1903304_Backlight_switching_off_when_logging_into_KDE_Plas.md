---
title: "Backlight switching off when logging into KDE Plasma Desktop"
date: 2012-01-02
forum: Desktop Environments
---

### Post by ubukool on 2012-01-02
Hi everyone,

Happy New Year!  I've got a problem with using KDE with Ubuntu 11.10 on an Acer 5336.  There is a general problem with Acer laptops anyway when using Ubuntu in that, at boot, the backlight is switched off but there are solutions for that which means that I can get it switched on again and the login screen shows up fine.  

If I log in to standard Ubuntu (Unity) there is no problem and the backlight stays on, but I wanted to try KDE, and when I try to login to the KDE Plasma Workspace, the backlight switches off again!  It's a bit annoying, to be honest.  To get the backlight working again requires running the command:

setpci -s 00:02.0 F4.b=00
 
I wrote a script for this and tried to get KDE Autostart to run it, but it won't because it needs to be run as root - result: my screen stays black!

Is there a way I can get KDE to run this script as root, or is there another way to run the command so that I can get my backlight on again?  I can't see to input the command into a terminal, which would be the other way to do it, but it's a pain!

Any help would be appreciated.

---

### Post by ubukool on 2012-03-22
For anyone else who is having this problem, here is an answer I found here:

[http://ubuntuforums.org/showthread.php?t=1864513](http://ubuntuforums.org/showthread.php?t=1864513)

Open a terminal and type in the terminal:

```
gedit ./etc/rc.local

```
This will open rc.local file. Now at the bottom make sure it looks like below and save.

```
sudo setpci -s 00:02.0 F4.B=00
exit 0
```

You should be fine, reboot and check it out.;)  

My system's backlight comes back on fine during boot up with this modification. There's also a really helpful script for switching the backlight back on when you 'wake up' from suspend or hibernate 

Good luck!

---

