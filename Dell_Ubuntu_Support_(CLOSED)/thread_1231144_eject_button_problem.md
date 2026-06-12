---
title: "eject button problem"
date: 2009-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rubaiyati on 2009-08-04
I hav a Studio 1537 with an optiarc dvd rom but the eject button doesn't work, pls help.

---

### Post by sharkbite1414 on 2009-08-04
Open a command line (Applications > Accessories > Terminal (in GNOME)) and type:

```
eject cdrom
```

to open your disk disk drive, if you have more than one disk drive you may need to specify a number as well eg. eject cdrom0, eject cdrom1, etc.

then type:

```
eject cdrom -t
```

to close your disk drive.

---

### Post by theGlitch on 2009-08-04
Check your keyboard short cuts. System->Preferences->Keyboard Shortcuts (this location could be wrong as I'm at work and not looking at my system). There should be a cd eject option; just double click the parameter (to the right) and push your eject button. It should set it correctly

---

### Post by Nathan_M on 2009-11-18
I'm having a similar problem, but the above solution doesn't solve it. When I press the eject button in the keyboard shortcuts screen, it doesn't detect that I've pressed it. $ eject cdrom0 works fine. Edit: I have an Inspiron 640m laptop.

---

### Post by teward on 2009-11-18
Are you talking about pressing the button on the drive itself, or through Linux?

If its on the drive itself that you're pressing and it doesn't work, its a hardware problem.

Otherwise, might be an incompatibility between devices.

---

### Post by Nathan_M on 2009-11-18
> **TrekCaptainUSA said:**
> Are you talking about pressing the button on the drive itself, or through Linux?

If its on the drive itself that you're pressing and it doesn't work, its a hardware problem.

Otherwise, might be an incompatibility between devices.

Yes, it is on the drive. And no, it's not a hardware problem, because it worked fine under Jaunty, it works fine when there's a CD in the drive (as opposed to a DVD) and when the drive is empty, and Googling has revealed that lots of people are having the same problem.

---

### Post by teward on 2009-11-18
i'll bet you its a problem deep within 9.10 Karmic.  So many problems are caused by it.  (don't yell at me for it, i still support ubuntu, but I think Karmic has too many problems).

---

### Post by soni1770 on 2009-11-19
also, if you just have one drice

eject


will work to, look, i just half'd your work load.:popcorn:

---

