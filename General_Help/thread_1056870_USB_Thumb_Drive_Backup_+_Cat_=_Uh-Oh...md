---
title: "USB Thumb Drive Backup + Cat = Uh-Oh.."
date: 2009-02-01
forum: General Help
---

### Post by ACMarina on 2009-02-01
My wife had moved the contents of her camera's SD card to my desktop, and I was attempting to move them from there to my thumb drive.  The copy dialog came up, it showed everything moving over, and when it "Finished" I went to grab a bite to eat.

Next thing I know, the cat is going crazy!  Seems he wrapped himself up in the power cord, unplugging the unit from the computer!  Now the photos are gone from the desktop, and they're also not on the thumb drive.  

Any thoughts on where to find them??  They have to have gone somewhere, right??

---

### Post by caljohnsmith on 2009-02-01
Does the thumb drive still mount OK, but it just doesn't show the pictures any more? If so, you could try running "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" on it to see what files it can recover. To use photorec you can do the following in a terminal:
```
sudo apt-get install testdisk
sudo photorec
```
Let me know how that goes or if you run into problems.

---

