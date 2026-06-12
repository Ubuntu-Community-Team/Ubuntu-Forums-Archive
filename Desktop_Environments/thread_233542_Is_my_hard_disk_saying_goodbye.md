---
title: "Is my hard disk saying goodbye?"
date: 2006-08-10
forum: Desktop Environments
---

### Post by mathjazz on 2006-08-10
As you most probably already know, after 30 boots disk check is forced. Today that happend on my computer and lots of errors showed up, all of them looking like this:

[TRATRA.LALALA] Buffer I/O error on device hda1, logical block TRALALA
[SOME.THING] hda: drive not ready for command

From time to time I also hear some strange beeps and voices from my hard disk. Some days ago my computer also started to crash for "no reason" and totally randomly.

I assume my disk is going to die soon.

Is that the case?

---

### Post by maniacmusician on 2006-08-10
it doesn't look too good, no. I dont have much experience with hard drive failures, but beeps and noises are never good, and those errors don't look too pretty either. whatever happens, my advice is to go get another hard drive and back everything up right away so you don't lose it all.

---

### Post by mathjazz on 2006-08-10
I already backed up everything, of course. ;)

---

### Post by maniacmusician on 2006-08-10
smart! how old is the hard drive anyways?

---

### Post by mathjazz on 2006-08-12
Hm, it's just about 4 years old.

---

### Post by chavo on 2006-08-12
You can also try smartmon for Linux [http://sourceforge.net/projects/smartmontools](http://sourceforge.net/projects/smartmontools) 

It will check your disk for any SMART related errors, assumin of course that your disk is SMART capable.

---

### Post by jchau on 2006-08-12
You can get the package "smartmontools" using the package manager and run it with the command "sudo smartctl -a /dev/hda" to get all the testing info for your harddrive.  (Assuming that the device name for your harddrive is /dev/hda)

---

### Post by jchau on 2006-08-12
A 4 year old harddrive should support SMART.

---

