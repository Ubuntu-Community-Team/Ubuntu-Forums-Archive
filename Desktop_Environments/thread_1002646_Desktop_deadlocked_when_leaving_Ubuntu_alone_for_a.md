---
title: "Desktop deadlocked when leaving Ubuntu alone for a while"
date: 2008-12-05
forum: Desktop Environments
---

### Post by dvdkhlng on 2008-12-05
Hi fellow Ubuntuers,

I recently installed Ubuntu 8.04.1 amd64 on my workstation (had previously used 7.04).  Now when I leave my computer for lunch, and return, the display is black, and the mousepointer invisible unless I move the mouse.  Looks like the 'blank' screensaver wreaking havoc.  I have to press ctrl+alt+bkspace and re-login to continue working.

I already unchecked 'Activate Screensaver when compute is idle' in the 'screensaver preferences'.  And set 'put display to sleep' to 'never' in power management prefs.  This doesn't help, unfortunately.

Switching to a console, while the Desktop is locked, I run 'pstree' but can't see any unusual running programs.  In my /var/log/syslog, I have lots of error lines:

Dec  5 13:22:15 kuehling kernel: [ 8892.800730] gnome-screensav[6161]: segfault at 21 rip 7f7da28ca8d4 rsp 7fffac185cc0 error 4

Strange, isn't it, given that the screensaver is disabled.  But could this explain the error?

I run the 'nv' xorg driver, and put the following lines into my xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "blabla"
        Busid           "PCI:1:0:0"
        Driver          "nv"
        Option          "Rotate"  "RandR"
        Option          "ShadowFB"  "on"
        Screen  0
EndSection

I configured 'Screen Resolution' to use Rotation: Left.

According to lspci, my graphics hardware is:

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

Any ideas what's going on?  If this is really the screensaver, then how do I completely force if off?  Any similar problems known?

Thanks for any help,
cheers,

David

---

### Post by dvdkhlng on 2008-12-08
Update: It just happened to me again, coming back from lunch, the desktop was blanked.  This time I switched to a console (Ctrl+Alt+F1) and issued

killall gnome-screensaver

which returned me to my desktop.  So is this really a problem caused by a non-responding screensaver?

David

---

### Post by druellan on 2008-12-08
On my Ibex, gnome-screensaver ALWAYS ask for a password after resume. Perhaps the problem is related to that: the relogin window is not showing up properly. Try typing your password and pressing enter to troubleshoot that.

---

