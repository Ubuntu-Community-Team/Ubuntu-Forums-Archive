---
title: "DVD player with ubuntu"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adamskiki on 2009-01-12
can anyone help me figure out this ubuntu program I want to watch DVD'd with an external Iomega cd/dvd player.  I talked to ubuntu support earlier they had me install gstreamer.  That did not help.  I still get a error saying it can not read the source. My computer is a Dell Mini 9. thanks

---

### Post by ugm6hr on 2009-01-12
This: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It is a very thorough walk-through of media issues.

However, a lot of it will not work with the Mini 9.

Try this first:
```
sudo apt-get install ubuntu-restricted-extras
```

If that doesn't work, try this:
```
sudo apt-get install gxine libxine1-ffmpeg
```

Then try using Gxine to play the DVD

If that also fails, you could try VLC:
```
sudo apt-get install vlc
```

Unfortunately, I suspect the missing component is actually libdvdcss2, which is only available on 8.10 in the lpia version [http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Whether the i386 Hardy version can be hacked for lpia - not sure: [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)

---

### Post by sandman652001 on 2009-01-18
try adding the Medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

They are in the process of adding support for the hardy lpia achitecture, once you have done search for libdvd and install the related files, it might help
anothe solution might be 
[http://shop.canonical.com/product_info.php?products_id=243&osCsid=284ec0d50217cb076d4a58d92f2ce739](http://shop.canonical.com/product_info.php?products_id=243&osCsid=284ec0d50217cb076d4a58d92f2ce739)
little pricey but.....

---

### Post by armandh on 2009-01-18
I used the regular medibuntu.org 5 easy cut and paste steps 
and got commericial dvds playing on an 8.10 mini-9

it did not work for me on the dell 8.04

---

### Post by sandman652001 on 2009-01-19
I have been talking with one of the guys at medibuntu and he has started adding lpia packages for hardy but not everything.

---

### Post by superm1 on 2009-01-19
> **adamskiki said:**
> can anyone help me figure out this ubuntu program I want to watch DVD'd with an external Iomega cd/dvd player.  I talked to ubuntu support earlier they had me install gstreamer.  That did not help.  I still get a error saying it can not read the source. My computer is a Dell Mini 9. thanks
If you purchase the DVD drive with the mini9, the disk that comes with it has a copy of Power DVD for linux.

---

