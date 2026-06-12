---
title: "Ubuntu will not load..Kinda"
date: 2009-03-03
forum: General Help
---

### Post by SymmetricalPanda on 2009-03-03
I just installed the most recent version of Ubuntu on my old IBM tower. I installed Ubuntu, everything went fine. Even before the installation I checked the CD for errors, all good. Every time I try to boot up it loads the Grub 1.5, and then goes to an orange background, my cursor pops up, goes to a black background and then freezes.I can't even move my cursor anymore. If anybody could offer any help it would be greatly appreciated.

Pentium 4 2.0ghz
2gigs of ram
on board video
No other OS

---

### Post by SymmetricalPanda on 2009-03-03
bump

---

### Post by oldos2er on 2009-03-03
From the grub menu, can you boot into recovery mode? What's the make/model of your video adapter?

---

### Post by SymmetricalPanda on 2009-03-03
> **oldos2er said:**
> From the grub menu, can you boot into recovery mode? What's the make/model of your video adapter?

I have actually tried recovery mode.Im not sure what the model is but I have had this motherboard since 2006

---

### Post by diwas on 2009-03-03
Well this might help.

Boot through the recovery mode and then select Terminal. Then there, remove compiz by the following commands
```

sudo apt-get remove compiz-core

```

And reboot
```

sudo shutdown -r now

```

Now boot normally, and test. 

Hope it helps.

---

### Post by SymmetricalPanda on 2009-03-04
This is starting to irritate me. Apparently I have to change the resolution because Its fixes most peoples problems like this but I don't have the slightest where to locate the command bar or anything like hat or how to do all this stuff.

---

### Post by diwas on 2009-03-04
Like I said earlier, boot through the recovery mode. It is there in the Operating System's selection menu (GRUB). I am sure u can do this.
And then after sometime (ie after u select the recovery mode) there will be options. Select Terminal (or command line, dont quite remember it sorry). And insert the commands as typed above.

---

