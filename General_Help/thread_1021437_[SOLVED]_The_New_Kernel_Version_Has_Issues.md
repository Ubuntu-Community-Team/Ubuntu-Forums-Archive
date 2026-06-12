---
title: "[SOLVED] The New Kernel Version Has Issues"
date: 2008-12-25
forum: General Help
---

### Post by Cadeyrn on 2008-12-25
I recently updated to the new kernel. The old one was 2.something with a 7 in it and the new one is 2.something with a 9 where the 7 used to be. So, anyway, the strangest problem that just showed up with this new kernel version is I get the same blinky-cursor-black-screen every time I start up that people get when their ATI Proprietary driver isn't installed correctly. This screen comes in the absence of a GUI right after Ubuntu starts up, so you never see or get to use the login screen or anything after that. I KNOW for a fact mine was installed perfectly a *long* time ago through:

```
sudo apt-get install xorg-driver-fglrx
sudo rm /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

followed by enabling my driver and restarting.

Anyway, just now I found the weirdest thing: I went into Recovery mode under the new version, and I tried choosing "resume" without doing anything else. Strangely, it showed me the GUI without any errors or uninstalling my ATI driver or anything. And before that I was using xfix, which, as always, complained about xorg.conf being changed and resetting it, which strangely also didn't tinker with my driver or its configuration. Not once have I ever heard of xfix being used without any installed video drivers disappearing.

---

### Post by Cadeyrn on 2008-12-26
Update: Starting last night, my computer is now only giving me that screen every other time I start up. This is a huge problem that needs to get fixed RIGHT now, because it's the same sequence of problems that happened spontaneously a while ago that screwed up my system and made me have to reinstall Ubuntu!!!

---

### Post by lsutiger on 2008-12-26
Just choose the previous kernel while Grub is loading...

---

### Post by Coder543 on 2008-12-26
When your computer turns on, you will see Grub begin to load and hit Esc. Then use the arrow keys to scroll down to the old kernel.

---

### Post by Cadeyrn on 2008-12-27
Argh, that would be just as annoying as entering Recovery mode. Could I just edit that section of boot.lst that says which boot mode to defaultly use?

Strangely, though, just now, I didn't get any errors two times in a row. Without Recovery mode or the new version. Maybe it's just a freak bug...?

---

### Post by Cadeyrn on 2009-01-02
Bah, it doesn't do this error all the time, so screw it. Solved.

---

