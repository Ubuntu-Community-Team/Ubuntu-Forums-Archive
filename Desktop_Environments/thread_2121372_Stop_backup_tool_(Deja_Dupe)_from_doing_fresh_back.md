---
title: "Stop backup tool (Deja Dupe) from doing fresh backups?"
date: 2013-03-01
forum: Desktop Environments
---

### Post by Yfrwlf on 2013-03-01
Full backups can sometimes take an extremely long time, for instance if you have a whole lot of data and/or the transfer speed to your backup location is slow.  At one time the Deja Dupe GUI allowed for adjusting when full backups occured, but in the new GUI it doesn't.

Why are full backups needed when you can do a checksum to verify the integrety of backup files?  Does Duplicity/Deja Dupe not have this ability?

If not, is there a way to turn off full backups?

Are there any other backup programs out there which have this feature?  Areca seems like it might be a pretty good Linux backup alternative.

If there is an issue with certain protocols doing remote file checksums, shouldn't it be enabled for SSH at least?

---

### Post by Yfrwlf on 2013-03-01
Solved!  As far as using an alternative is a solution, at least.

[http://www.duplicati.com/](http://www.duplicati.com/) solved all my problems.

Duplicati recommends doing periodic full backups, but due to the nature of my backups this is not a big concern.  With Duplicati I can make full/fresh backups occur as frequently as I want, unlike Ubuntu's oversimplified version of Deja Dupe.  (for anyone confused by the custom field for this in Duplicati, do 1Y for 1 year, 3M for 3 months, etc)

I have no problem with devs making clean and simple interfaces, that is a good thing, but I do have a huge pet peeve with completely removing advanced features instead of tucking them into the application somewhere.  The mentality of destroying features that some users want just because you don't know how to cleanly work them into your interface is a plague.

---

