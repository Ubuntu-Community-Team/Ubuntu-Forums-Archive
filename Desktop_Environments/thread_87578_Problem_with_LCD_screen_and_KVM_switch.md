---
title: "Problem with LCD screen and KVM switch"
date: 2005-11-08
forum: Desktop Environments
---

### Post by mandrake on 2005-11-08
I'm using the latest Ubuntu.  The LCD screen is Dell, but I'm not sure of the model (it's a hand me down).  The KVM switch is a Master View Mini KVM switch by Aten.  The problem is that X doesn't get the correct screen resolutions, it only sees 320x240 or 640x480.  This of course, causes viewing problems.

Any suggestions?

---

### Post by stevea1210 on 2005-11-09
first, I would hook up the pc directly to the monitor without the KVM.  Let us know if the problem exists without the kvm.  that will eliminate some possibilities.

Does it do this if you boot the pc up while the kvm has that box selected?
Does it do it if you boot the pc  up while the kvm is on another pc?

---

### Post by meep on 2005-11-12
How did this work out for you Mandrake?  I have a kvm and lcd and will be install Breezy on one of the systems attached.  

It works fine with Hoary, though.

---

### Post by meep on 2005-11-13
Worked fine on my installation.  I now have Hoary on one system, and a fresh install of Breezy.  Both are working with the KVM switcher, the LCD, and the mouse perfectly. 

I had problems with my mouse going nutso in Hoary.  Under Gentoo it worked fine, but when I switched to Hoary, I'd have to reboot.  Here's the thread:   [http://ubuntuforums.org/showthread.php?t=6550](http://ubuntuforums.org/showthread.php?t=6550)

I'm happy to say that although I had to make that change on Hoary, the mouse (and LCD) worked right for the start on Breezy! :)

---

### Post by meep on 2005-11-13
After another reboot, I had the same problem.  Screen Resolution was only 640x480. 

I modifed /etc/X11/xorg.conf and added the Vert and Horiz Refresh lines for my monitor.  I was able to pull them out of the file from the Hoary installation.  Handy.  I added the lines to the "Monitor" section, like so:

        HorizSync       30-81
        VertRefresh     56-75

Another reboot, and it's working again.

---

