---
title: "[SOLVED] Synaptic's updates have broken my display -- black screen after boot"
date: 2009-01-12
forum: General Help
---

### Post by Hsere on 2009-01-12
I recently succeeded (with the help of a few people in this forum) at getting my graphics card and monitor to work properly.  [Original thread here.]("http://ubuntuforums.org/showthread.php?t=1024465")  For the last week, it's been working fine.  Synaptic installed a set of updates today (the only thing it asked to override was the boot menu, and I denied it permission to do so).  Now after Ubuntu boots, it just goes to a black screen, and the monitor seems to shut on and off until I reboot the machine.  It doesn't even offer me the option of Low-Graphics Mode.

I booted into Recovery Mode and used the xfix function, which reset my xorg.conf file to the default.  Ubuntu seems to boot properly now, but I'm back to using an incorrect resolution and being unable to use my graphics card.  I'm in essentially the same predicament I was in when I posted that original thread.

I tried resetting my xorg.conf to the previous version, which worked until Synaptic ran its updates (the version at the end of my original post).  It still gives me the black screen, which indicates to me that something other than my xorg has changed.  When I switch it back to the basic default, Ubuntu boots.

Any ideas?

EDIT: Forgot to mention; I know Ubuntu finishes booting (watched the sequence with "quiet splash" turned off).
EDIT2: The same thing happens if I manually change the monitor and video driver settings using ```
gksudo displayconfig-gtk
```.  Also, if I change the settings and then use "test," it goes to the black screen and doesn't return as it usually does if "Keep These Settings" is not clicked.

Also, the screen doesn't actually turn on and off indefinitely.  It just turns off and on twice and then stays at the black screen.

I've heard of things like this happening with 8.10, but I'm still using 8.04 -- I just installed the regular Syanptic updates, and the Version and Release Notes confirm that I'm still using 8.04.

---

### Post by Hsere on 2009-01-13
Never mind.  Problem fixed.  I just reinstalled the ATI drivers.  I should do the obvious fixes before posting.

---

