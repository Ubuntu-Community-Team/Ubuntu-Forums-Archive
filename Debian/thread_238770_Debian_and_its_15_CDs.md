---
title: "Debian and its 15 CDs"
date: 2006-08-18
forum: Debian
---

### Post by Klaidas on 2006-08-18
Hi there ;)
Well, one day I thought I should try Debian, but when I went to the download page, I saw those 15 CDs, and I was like o_O

As I understand, all those CDs contain extra software for debian?
If so, how much should I download? 
Which is the default install CD like Ubuntu has - one CD with basic apps?

---

### Post by meng on 2006-08-18
There's a netinst version on 1 CD, which as the name suggests grabs the packages over the interweb :p.
Here's one place:
[http://www.us.debian.org/devel/debian-installer/](http://www.us.debian.org/devel/debian-installer/)

---

### Post by tonym on 2006-08-18
As an alternative to the 15 CDs there is the 2 DVD set.  In either case you just need disk 1 to install.  Any packages not on disk 1 will be pulled in from the network.

---

### Post by fluffnik on 2006-08-19
Provided you have a decent network conection all you need is the netinstall image which is 100-150MB.

If you are installing several machines with the same software you might want to set up a local partial mirror or make CDs of the packages *you* use with apt-move.

It's unlikely that you'd want more than the first two CDs even on dialup since the more popular a package is the earlier it appears in the CD set.

Debian also uses a tool called jigdo which generates up to date isos rather than snapshots.

Most likely you just want the latest netinst image.  :)

---

