---
title: "different usplash problem"
date: 2005-10-31
forum: Desktop Environments
---

### Post by dauvm on 2005-10-31
OK, I have a little problem with usplash that I think is different than the others I've read.

When I was still using hoary, I downloaded the 5.10PR live-cd and really liked the usplash. Then when I upgraded, I did a clean install, and it did the usplash thing correctly while installing. However, on first boot and since then... after I select ubuntu in grub, the first thing I see is "vesafb.ko not found" or something... followed by a few more errors. I'm not really sure. Anyways, I just don't get any usplash at all... doesn't even try it.

I've also tried apt-getting a different kernel, reinstalling usplash, and then rebuilding the boot image... still seems to be missing that file for my fb. I'm not sure what log file to look in to find that error message, but I did **cat kern.log |grep vesa** and everything that came up looked like I have a running fb.

Not sure if it makes a difference but my laptop is one of the ones that almost always takes the vga=771 on boot, so that's what I ran when I installed ubuntu. Would that make a difference of how it installed usplash?

Thanks,
-Doug

---

### Post by santo on 2005-11-02
I'm experiencing the same problem on my brand new Dell Inspiron 9300 laptop
(just got it today :D )

I also had to use the vga=771 option to get the installer running

On my previous laptop (Acer TravelMate 8003LMi, which was stolen 2 weeks ago), I didn't have this problem.
Didn't need to provide the vga=771 boot option for that laptop.

Installation was done with the same cd, so that can't be the problem.

Any suggestions ?

---

### Post by santo on 2005-11-04
The exact error message is:

```

insmod: can't read '/lib/modules/2.6.12-9-686/initrd/vesafb.ko': No such file or directory

```

but the file is there:

```

user1@laptop01:~$ ls -lF /lib/modules/2.6.12-9-686/initrd/
total 24
-rw-r--r--  2 root root  6879 2005-10-10 15:17 capability.ko
-rw-r--r--  2 root root 13902 2005-10-10 15:17 vesafb.ko

```

and everyone has read permission, so that can't be the problem I think :confused: 


Note: when I remove the boot-option "vga=771" from grub, I don't see the error message, but also I don't get the usplash screen.
Just a blank screen until gdm is loaded.
(-> the error message probably is still there, but I just can't see it)

---

### Post by Moebius on 2005-11-07
Same "problem" here as santo, well not really a problem but an anoyance with that.

Did this change from Hoary to Breezy? Cause in Hoary it worked fine, even if then we didn't have an official usplash.



EDIT: While searching it seems that one component of the boot process is broken and ignores the "vga=" line

---

### Post by dauvm on 2005-11-07
So looks like everyone that has this problem is booting with vga=771 on boot.

I have a hp pavilion zx5000 (laptop) with a 1280x800 widescreen, and radeon mobility 9200. What does everyone else have for monitor/graphics card combo? I'd love to get to the bottom of this...

---

### Post by Abel Hernandez Zanatta on 2005-11-08
Well I had the same problem about the vesafb.ko not found but I solved the problem taking a look at bugzilla.

You can take a look at bug 17331:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17331](http://bugzilla.ubuntu.com/show_bug.cgi?id=17331)

Basically you need to add a line to the usplash script and run
dpkg-reconconfigure linux-image...............

---

### Post by santo on 2005-11-10
Thanks Abel, that was it.

But why there are 2 vesafb.ko files and why usplash is pointing to the "wrong" one is still not clear to me.

As someone mentioned in the bug report, it's not related to only new installations or only upgrades, I have noticed this with both an upgraded Ubuntu breezy and a clean installation (this one).
On another machine, the upgraded Colony 3 didn't have the problem.

---

### Post by dauvm on 2005-11-12
Yea, thanks for that link, Abel... that worked fine for me. I had checked launchpad but forgot about ol' bugzilla.

Actually, it looks kinda crappy on my widescreen monitor anyways :( but... I'm sure they're working it... I can be patient

thanks again,
-Doug

---

