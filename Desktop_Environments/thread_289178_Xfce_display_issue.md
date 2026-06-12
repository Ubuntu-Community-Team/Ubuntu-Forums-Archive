---
title: "Xfce display issue"
date: 2006-10-30
forum: Desktop Environments
---

### Post by wussie on 2006-10-30
ok, I updated my Xubuntu last night and then restarted the computer today.  Now for some reason I am stuck at what appears to be 640x480.  I cannot change resolutions using the display manager built into Xfce, there are no resolution settings displayed in the manager at all.  How do I go about fixing this?  I am a relative Linux newbie, but am not afraid of the command prompt, so lay it on me in simple to follow steps please.

---

### Post by ceargle on 2006-10-30
Post the output of ```
dmesg
```  It lets us know what kind of hardware you're using.  

You may want to try ```
sudo dpkg-reconfigure xserver-xorg
``` first, then press Ctrl+Alt+Backspace to restart X and see if that fixes your resolution problem.  If not, editing the /etc/X11/xorg.conf file may be necessary.

---

### Post by wussie on 2006-10-30
I ran the xreconfigurer and I can change my resolution, but now all the fonts are tiny!

---

### Post by ceargle on 2006-10-30
If you go to the XFCE Menu--> Settings--> User Interface Settings you can set the default font and size there.

---

