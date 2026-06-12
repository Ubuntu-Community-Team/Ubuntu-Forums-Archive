---
title: "Gutsy, XPS2 and LED lights"
date: 2008-01-24
forum: Dell  Ubuntu Support
---

### Post by boomix on 2008-01-24
I love Linux on this laptop it is allowing me to learn all I've wanted to know about ubuntu and developing on it. However LED lights drive me mad. I would like to be able to change them from within Ubuntu instead of messing with it in bios. 

I've been looking for past month for drivers or utility that would allow me this. Any help would be appreciated.

Thanks.:confused:

---

### Post by m94mni on 2008-01-25
In the package libsmbios-bin, there is a utility called dellLEDCtl

Use like

sudo dellLEDCtl --zone1 2

see  

dellLEDCtl --help

The libsmbios package is provided by Dell, so many thanks to them!

---

### Post by Nunslaughter on 2008-01-28
Check this thread: [http://ubuntuforums.org/showthread.php?t=616864](http://ubuntuforums.org/showthread.php?t=616864)

---

### Post by drsaamah on 2008-02-05
Hm... this is not working for me.  Is this exclusively for the m1710?  I have a Dell m1330a dn it doesn't seem to be doing anything.  Any help would be greatly appreciated.

---

