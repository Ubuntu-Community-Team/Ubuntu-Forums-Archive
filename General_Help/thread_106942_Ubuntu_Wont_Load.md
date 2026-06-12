---
title: "Ubuntu Wont Load"
date: 2005-12-21
forum: General Help
---

### Post by dreamingxashley on 2005-12-21
I just installed Linux (for the 3rd time), and it wont load. I get these two errors:

*/dev/dhe5 does not exist. Dropping to shell.*

then theres some stuff about a busybox...

*/bin/sh: cant access tty; access control turned off*

Not sure about the access control part, but the turned off part is right.

So, what do I do here? Id rather not reinstall for a 4th time, as Im sure it will just give me the same errors. I resized my OS drive, and gave Linux 2.1gigs of space...

:KS (love the little star!)

---

### Post by -deadcats on 2005-12-21
Screech! Are you sure 2.1 GB is enough space for what you want to install? 

Most modern Linux distros need a minimum of around 5GB, more or less, and more is always better. And another sizable swap partition, also, depending on your needs.

How 'bout some hardware specs and what you want to accomplish, please? :)

-dc

---

### Post by psoleko on 2005-12-21
Also have you tried burning a new installation cd at a slower speed, perhaps some files did not get copied over due to not being able to be read.

---

### Post by dreamingxashley on 2005-12-21
Hmm... since when did Linux become a space hog? lol

Specs... AMD proc, 500something ram, 80gigs of HD space, most of it, currently just the space where Windoze is installed..

As for usage, word processing, watching movies, downloading, internet, chat, irc, basic stuff...

Ill try giving it more space see what happens.

---

### Post by dreamingxashley on 2005-12-22
Well... I tried giving it more space, this time with nearly 12 gigs, which then gave the swap space 512megs. And it still wont load. This time it says HDE2 doesnt exsist.

---

### Post by BathroomNinja on 2005-12-22
2 things.  First, boot from a Live CD, then run fdisk on your HD.  I want to see how many Hard drives you have and how many partitions. 

run it like this:

```

fdisk -l /dev/hda

``` 

also try
```

fdisk -l /dev/dhe

``` 
  Because I'm trying to figure out what drive dhe is.



2nd, make sure to run the test on the install media before installing.  I have burned a number of bad install CD's.

---

