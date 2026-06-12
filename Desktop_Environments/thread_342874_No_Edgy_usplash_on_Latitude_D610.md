---
title: "No Edgy usplash on Latitude D610"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Kensey on 2007-01-20
After upgrading to Edgy, I don't get a usplash anymore.  At boot, on vt1 I get an error that no theme was found for 1400x1050 (I have a Latitude D610 laptop with that native resolution, which I have to run 915resolution to use in Gnome).  I've changed /etc/usplash.conf to X=1280 and Y=1024, with vga=771 in the kernel arguments in /etc/grub/menu.lst, but I still get this error.  How do I fix it and get a spiffy usplash again?

---

### Post by JamieC on 2007-01-20
Try opening a terminal window and running the following:
```

sudo dpkg-reconfigure linux-image-`uname -r`

```

What is the output?

---

### Post by Kensey on 2007-01-21
Funny.  I had done dpkg-reconfigure, which I thought took care of rebuilding the initrd, but when i rebuilt it by hand like you suggested it worked.

Well, sort of.  It still complains about not finding a theme, but now it's complaining about not finding a theme for 1280x1024, so things are on the right track :)

I assume from bits and pieces of other threads I skimmed that usplash has changed significantly since dapper -- in particular I remember that dapper's usplash only supported art of 640x400 or 640x480 at 16 colors.  Is there a comprehensive guide to new usplash capabilities and how to create art for it?

---

### Post by Kensey on 2007-02-14
Still no dice.  I set the vga option in /boot/grub/menu.lst to 771 (640x480), set the resolution in /etc/usplash.conf to match, sudo dpkg-reconfigured the kernel image and did sudo update-initramfs -u.  The only difference is now it complains about not finding a theme for 640x480.

---

### Post by PapaWiskas on 2007-02-15
This seems to be a real problem with no real answer.
I have the same issue, went from Dapper to Edgy via the recommended gksudo upgrade method.  After that Usplash no longer works.....

I have even formatted the harddrive and done reinstalls, and still no dice.
Why is there no answer for this?

---

### Post by roderikk on 2007-03-04
Hi,

I just did an update too and found that usplash is not installed. When I try to use aptitude to install usplash it wants to remove all 350 or so xorg related packages.

Is there any way to get the usplash back?

---

### Post by roderikk on 2007-03-04
Hm, I just found out that apparently the ubuntu-desktop package wasn't installed. I am trying to install this now and hope this will solve the problem.

---

