---
title: "Xubuntu 7.10 screen saver problem"
date: 2007-10-22
forum: Desktop Environments
---

### Post by headcronie on 2007-10-22
Long story short - my *old* ATI Rage 128 video card chokes and dies a horrible death upon launching the "Molecule" screen saver.  

In 7.04, we could select each screen saver we wanted to use in random mode, so I just unchecked the "molecule display".  In 7.10 we cannot.  Thus, the "molecule" one is used, and causes a system freeze.

Can anyone point me to the configuration file for the screen saver utility, so that I can remove the malfunctioning "molecule"?

Please keep in mind - I'm using Xubuntu.  :)

Your help is greatly appreciated.  

Thanks in advance.  :)

---

### Post by headcronie on 2007-10-23
Bump bump.  Anyone?

Does my question make sense?  Do I need to elaborate more?

---

### Post by hpp3 on 2007-10-29
Apparently Xubuntu uses gnome-screensaver now instead of xscreensaver, which is the interface you're used to.

Do one of the following:

1- Do a 'locate' for the molecule screensaver. Once you find it, rename it 'molecule.off' and logout/login. Check your screensaver preferences to see if itshows up again, hopefully not.

2- Uninstall gnome-screensaver and  install xscreensaver. Obviously your screensaver function is working, so this might be overkill, but at least you'll have your old interface back. Also take a look at this thread: [http://ubuntuforums.org/showthread.php?p=1727716](http://ubuntuforums.org/showthread.php?p=1727716)

My problem was that the screensaver simply wasn't coming on (just a blank screen) and I hated the gnome-screensaver interface so I went with #2.

---

### Post by BigBananaMan on 2008-05-27
I tried option 2 which didn't work for me.  When I selected molecule under xscreensaver it caused the same problems that headcronie had except that my computer would freeze just from seeing that little preview, this prevented me from going back and deselecting the screensaver.  I reinstalled gnome-screensaver and tried option 1 to remove that molecule and it worked like a charm.  Thanks a bunch hpp3!

---

