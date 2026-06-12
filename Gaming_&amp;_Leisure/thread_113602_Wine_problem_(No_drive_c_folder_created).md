---
title: "Wine problem (No drive_c folder created)"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by cohan on 2006-01-06
This is my first post in this forum. Hello everyone=)

Here is my problem, I've recently installed the newest wine version, and when i go into "winecfg" and go to Drives I get this message "You don't have a drive C. This is not so great. Remember to click 'Add' in the Drives tab to create one". But when i try to do that it just creates a shortcut to "../drive_c". I clicked Apply and tried to restart winecfg but same message when I went to the Drives tab, and the drive_c shortcut was gone.

I tried reinstalling, updating and completly removing in Synaptic but with no luck. I think the problem has to do with that there might not be a drive_c folder to mount. 

Can anyone help me? Thanks in advance.

Cheers!

---

### Post by aysiu on 2006-01-06
Drive C is probably in /home/cohan/.wine/drive_c

It's a hidden folder.

---

### Post by stratotak on 2006-01-07
just wondering??had you run wine before you tried to run winecfg??..cause i think your .wine  directory in home folder isnt created till you run wine for the first time..when i install wine and first time i use it i type in wine at console and it says its creatinng direcotory..not in those words but basically thats what its doing..so if you installed wine then ran winecfg first..maybe the reason it showed you had no c_drive was because it hadnt created it yet in you .wine home directory..maybe that what happened??

---

### Post by handy on 2006-01-07
WineTools, is worth installing, it will give you an easier & more capable Wine config.

Take my advice & don't install IE6, it cannot be separately uninstalled, unless you get stuck into the registry in Wine, & it upsets the graphics display if you run DVDshrink:confused: 

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

All the best :p 

handy

---

### Post by cohan on 2006-01-07
Thanks for the help everyone.

stratotak, I think that was the problem, I tried starting a program in wine and then ran the winecfg and it worked =D 


Cheers!

---

