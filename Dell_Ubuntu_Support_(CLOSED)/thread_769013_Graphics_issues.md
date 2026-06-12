---
title: "Graphics issues"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by swebuntuden on 2008-04-26
I just installed 8.04 and have ran into trouble with my graphics card. Whenever I enable the driver and reboot, the screen remains white with black lines at the bottom. This does not go away at all. I am therefore forced to reinstall Hardy, which I have done 3 times today because of this. I don't know what to do and I am still new to Ubuntu. Can someone please help me? I really want all the neat eye-goodies! 

By the way, my model is Inspiron 1520, with 8600M GS graphics (I think...)

---

### Post by Scheater5 on 2008-04-26
I don't have a solution to your problem, but I have a workaround to prevent you having to reinstall.  On bootup, press ESC to enter the GRUB menu, and select the "recovery mode" kernel.  When the blue screen comes up, select "xfix."  
Let it do it's thing, and the blue screen will come back up - select to do a normal boot, and you will be presented with all your graphical goodness, minus your restricted drivers (actually, it will boot from the last working xorg.conf, if I understand correctly).  Apparently there's still a bug with the nvidia drivers  in 64-bit - is that what you are using?

---

### Post by swebuntuden on 2008-04-26
I don't know ... I have an Intel Centrino circuit and Core 2 Duo CPU. Downloaded the x86 image, was that the right one?

---

### Post by Scheater5 on 2008-04-26
You have a 64bit processor, and you're using the 32bit version of Ubuntu.  That's fine - you can do that.  You probably won't notice a difference at all unless you do some processor intensive work like 3d modeling or music processing.  Most people recommend 64 bit if you have a 64 bit processor - and I do too - but 32 bit will work just fine.  
All that means is that I have no idea what your problem is - the only bug I'm familiar with deals specifically with 64 bit and nVidia (bug #140908 ).  But, if you try and install the driver again, and X freaks on you, then follow my instructions above and you'll be back with a working system.

---

### Post by x3haloed on 2008-04-26
I have the same laptop (but with 8400M GS) with the same exact problem. I had the same issue with 7.10, and I was able to resolve it somehow, just don't remember how. I am trying to retrace my steps and figure it out. Any help is appreciated!

---

### Post by LeoSolaris on 2008-04-26
That is fairly odd...  I have the 1520 with the GS 8400, and I never had any issues out of it with the 32 bit system. Just to check, do you guys know for sure that your cards are working properly? It may be a case of bad cards rather than bad drivers.

I wasn't aware that the card had a nasty bug in 64 bit. I will have to remember that.

Leo

---

### Post by x3haloed on 2008-04-26
I am running x64.
I just got it fixed. Had to install the new nvidia beta driver.
[http://ubuntuforums.org/showthread.php?t=712479&page=5](http://ubuntuforums.org/showthread.php?t=712479&page=5)
Also, I had to make a /usr/lib32 symlink that points to /usr/lib to get nvidia's installer to work right.

---

### Post by atropos90 on 2009-09-19
Real may be...

---

### Post by Elfy on 2009-09-19
closed - grievous case of necromancing going on

---

