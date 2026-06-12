---
title: "BIOS update for 1420n?  Currently at A00."
date: 2010-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cheetaux on 2010-06-20
I have 3 PC's running Ubunutu: a Dell Dimension E510 desktop, a Dell 1420n laptop, and a no-name PC (running Xubuntu).  When I did a ssh login to my 1420n laptop, I got the following message:

```
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose
```


I looked into it and found out that my 1420n is running BIOS version A00.  Searching the Dell website, I found that the latest BIOS version for the 1420 is A10.

Is it recommended that I update the BIOS?

---

### Post by hwertz on 2010-07-04
Well, to be honest the NX support (non-execute) is more an additional layer of security than something I'd lose sleep over not having... it's to prevent someone from using a buffer overflow to put stuff onto the stack and then execute it.   Almost all my systems are old Socket As and are too old to have it, and the one that "could" have it is in the same boat as your box -- the BIOS disables it.    

     That said, I'm looking into using these instructions [http://java2go.blogspot.com/2010/05/how-to-upgrade-your-dells-bios-directly.html](http://java2go.blogspot.com/2010/05/how-to-upgrade-your-dells-bios-directly.html)

      to update my box.   You can update the BIOS directly from Ubuntu, and it's safe -- it loads the new BIOS into memory, and when you reboot it checks the copy is complete and uncorrupted (so you can't have some system crash end up with you having a halfway-flashed system.)

---

