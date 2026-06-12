---
title: "i have a CD-RW/DVD+RW drive... BUT I CAN'T BURN DVD'S?!?!?!? HELP!"
date: 2009-04-21
forum: General Help
---

### Post by Ozzy0sbourne on 2009-04-21
i have a CD-RW/DVD+RW drive...
and ubuntu also reads it exactly like that.
but all programs ive tried says i don't have a disc when i insert a blank disc.

any ideas on how to get it to work?

thanks in advance. ;):D:):P:KS

---

### Post by zero777zero on 2009-04-21
does the drive read regular discs (CDs, DVDs)?

---

### Post by Ozzy0sbourne on 2009-04-21
> **zero777zero said:**
> does the drive read regular discs (CDs, DVDs)?

yes.
it can play dvd's and can play cd's.

---

### Post by zero777zero on 2009-04-21
its probably having a problem with your brand of DVD-R. i'm assuming you tried to see if brasero (default burning app) works

---

### Post by Ozzy0sbourne on 2009-04-22
> **zero777zero said:**
> its probably having a problem with your brand of DVD-R. i'm assuming you tried to see if brasero (default burning app) works

yes.
ive tried nero... brasero... and a bunch of others...

i've tried all of the dvd+rw/dvd-r ETC.

it worked when i had windows.

---

### Post by boof1988 on 2009-04-22
If you want to try using terminal commands to burn a disc, it may show some more information on what is the problem.

If you want to try *cdrecord* (it is installed by defualt with Ubuntu and Xubuntu IIRC).  I have burnt DVDs using the following even though the device indicates */dev/cdrom*...
```
cdrecord -v dev=/dev/cdrom file-to-burn.iso
```

You may need to change the device (though probably not).  And you will need to use the real name for the file you want to burn (instead of the "*file-to-burn.iso*" above.

The following may give you some more information on using cdrecord...
```
man cdrecord
```

HTH

---

### Post by bacchusmarsh on 2009-04-25
i have the same problem burning to cd-r.
My drive works fine with playing cds and dvds, but this is the first time trying to burn with Ubuntu (default burner brasero. i looked at the manual and info in command line but not much help.)

The brand of cd-r is mag media

---

