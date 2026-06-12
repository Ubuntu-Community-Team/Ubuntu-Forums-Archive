---
title: "Blank screen on Xserver restart"
date: 2007-02-19
forum: Desktop Environments
---

### Post by Sellout on 2007-02-19
I ran into this problem after uninstalling beryl a few weeks ago. i've searched around for a solution but can't seem to find one. 

When i first boot into the system, everything's fine, no issues. If I restart xserver (ctrl+alt+bkspace) then login, i hear the start up sound, i can see and move my mouse, but nothing else loads.  I can restart the xserver again and try again but get the same problem. I can't even load a failsafe session. the only way to fix the problem is to restart the entire computer. 

any thoughts? 

edgy/fglrx/x800xt/x86-32bit.

---

### Post by erkki70 on 2007-02-19
Hi,
You should have a look to your xserver log ( /var/log/Xorg.0.log) file as it will point to errors and probably give a starting point debugging.
Just an idea though...

---

### Post by Sellout on 2007-02-19
when i compare the log from a successful boot and from when i restart X and have it "hang" the only difference is in the last lines of the log for the bunk restart i get:

(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xd000 at 0xb7707000

means nothing to me tho.

---

### Post by Sellout on 2007-02-20
bump

---

### Post by georgekurian80 on 2008-01-05
Hi

I am new to ubuntu. when i start my ubuntu os in my dell laptop xserver is not starting. when i start it manually it gives a white blank screen. i not able to find out the reason by looking in to the log file. please help me

i am attaching  my log file also

thanks in advance

---

### Post by ChameleonDave on 2008-01-05
I have had this problem too.  

Also, I can't get any terminal sessions by hitting Ctrl + Alt + F1, etc.

---

### Post by magic_ninja on 2008-01-05
Other people have had this problem, check this link, it seems that an install from the alternate cd would help
[http://ubuntuforums.org/showthread.php?t=568105&page=2](http://ubuntuforums.org/showthread.php?t=568105&page=2)

---

### Post by ChameleonDave on 2008-01-05
> **magic_ninja said:**
> Other people have had this problem, check this link, it seems that an install from the alternate cd would help
[http://ubuntuforums.org/showthread.php?t=568105&page=2](http://ubuntuforums.org/showthread.php?t=568105&page=2)

Hmmm, but I don't want to reinstall.  Actually, I'm fairly sure that it used to work, back when I first installed the OS.  Something must have got knocked out of place when I added certain things in Synaptic.

What files control such things, and what are their default settings, so that I can repair the problem?

---

### Post by Ptero-4 on 2008-01-05
type sudo dpkg-reconfigure xserver-xorg in the terminal. This will reset the /etc/X11/xorg.conf file (this is what controls the ubuntu GUI) to default settings.

---

### Post by ChameleonDave on 2008-01-05
> **Ptero-4 said:**
> type sudo dpkg-reconfigure xserver-xorg in the terminal. This will reset the /etc/X11/xorg.conf file (this is what controls the ubuntu GUI) to default settings.

In my case, at least, I don't think that's the problem.  Most of the time, I can get back to an X session.  The main problem is that my tty consoles are not available.  It must be some sort of gdm-related setting.

---

