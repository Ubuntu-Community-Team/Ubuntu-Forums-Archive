---
title: "System hangs at boot"
date: 2006-06-06
forum: Desktop Environments
---

### Post by katiad on 2006-06-06
I did a fresh install of Dapper last night. Had some issues with the nvidia drivers, like a billion other people, but everything, finally, started working correctly. 

But today, I had to reboot the system and ran into a problem. It hangs at Starting Hardware Abstraction Layer for several minutes before suddenly coming to life again.

Then, (I'm not sure this is related) when I logged in and the desktop came up, a minute later, a box popped up saying: "Error - KDE Panel:  The process for the system protocol died unexpectedly." Then X restarted. Logged in again, got the same error, but X didn't restart.

What on earth is going on, and how can I fix it? :) Thanks.

---

### Post by katiad on 2006-06-07
Boy, this forum is moving fast. *bump*

---

### Post by tseliot on 2006-06-07
Can you try my script? I have just released version 0.36. It might do the trick for you.

---

### Post by katiad on 2006-06-07
That definately didn't do the trick... I did give it a try, but it gave me nothing but more trouble - hung indefinately during startup. Uninstalled it... same problem. Now hangs indefinately - gets past the HAL problem and makes as if to continue starting up, but hangs with nothing but the ubuntu startup logo and the progress bar.

---

### Post by katiad on 2006-06-08
I reinstalled nvidia-glx and the restricted modules, which at least allowed me to log into the computer once more without going through the recovery mode. But startup takes about 10 minutes once it hangs.

Did manage to catch this error message, if it helps:

> /etc/dbus-1/event_d/20hal exited with return code 2

Er. May have been event.d  <--- not entirely certain - I had to write fast.

---

### Post by katiad on 2006-06-08
Solved. Turns out that automounting samba shares in /etc/fstab causes some conflict with hal, creating this hangup. Just putting in noauto in the options in /etc/fstab for each of my shares solves the problem, though I /do/ have to mount each one of them by hand.

Anyone know how to make this work without requiring sudo?

---

### Post by j0rd on 2006-06-09
same issue.

---

### Post by j0rd on 2006-06-09
[QUOTE=katiad]Solved. Turns out that automounting samba shares in /etc/fstab causes some conflict with hal, creating this hangup. Just putting in noauto in the options in /etc/fstab for each of my shares solves the problem, though I /do/ have to mount each one of them by hand.[/QUOTE]

Removed my smb-automounts and it fixed my issue. Thanks for the heads up.

---

### Post by jinxed on 2006-06-10
[QUOTE=katiad]Solved. Turns out that automounting samba shares in /etc/fstab causes some conflict with hal, creating this hangup. Just putting in noauto in the options in /etc/fstab for each of my shares solves the problem, though I /do/ have to mount each one of them by hand.

Anyone know how to make this work without requiring sudo?[/QUOTE]

Same problem here. Adding noauto does speed up the boot and correct the hanging hald, but now I must manually mount my Samba shares. ](*,) Any idea how to get around this? :confused:

---

### Post by Daniel Ibrahim on 2006-06-22
I also have a hang after the **[COLOR="Red"]hald[/COLOR]**, however, my hang is complete, it doesn't complete the boot and I end up with a blank screen, please see on  a different thread (sorry I hadn't found this thread here when I posted the other one...: [http://ubuntuforums.org/showpost.php?p=1166898&postcount=3](http://ubuntuforums.org/showpost.php?p=1166898&postcount=3) )

I have also found more references to this on:
[http://ubuntuforums.org/showthread.php?t=198225&highlight=Hardware+abstraction+layer](http://ubuntuforums.org/showthread.php?t=198225&highlight=Hardware+abstraction+layer)
this one also includes a solution to the problem by changing the xserver configuration

[http://www.ubuntuforums.org/showthread.php?t=192025&highlight=hald](http://www.ubuntuforums.org/showthread.php?t=192025&highlight=hald)
is a post that  includes this problem with smbfs, too,

however I don't have samba shares, and these problems with the other things suggest that it is in fact the Hardware abstraction layer daemon (hald) that causes us all this trouble.

Any suggestions from a developer? I am sorry but I have not yet got the Ubuntu machine online and I can only download a single package or handcode a bugfix. Please anybody tell the solution.

---

### Post by kzutter on 2006-08-20
> **jinxed said:**
> Same problem here. Adding noauto does speed up the boot and correct the hanging hald, but now I must manually mount my Samba shares. ](*,) Any idea how to get around this? :confused:

I fixed this YAY!! I now boot past hald AND have my samba mounts!
:p 
Changed the filesystem type from smbfs to cifs in my fstab entries.
Seems that smbfs is being deprecated - CIFS is the new hot sh*t
Also had to change some of the options ( see man mount.cifs) - basically same settings, just uses differnt names for the options (file_mode insteadn of fmask, etc.)

Also had some permission problems - seems that smbfs is lame about unix permissions, but cifs does them. I want all new files to be 0777, but cifs was using my umask and ignoring my file_mode=0777 option - I had to turn off unix extensions on my samba server smb.conf (unix extensions = no) so that file_mode would work the way smbfs used to handled it.

---

