---
title: "Wiping (unused) disk space"
date: 2006-08-20
forum: Desktop Environments
---

### Post by qrwe on 2006-08-20
Hello,

I primary wonder if anyone has a good suggestion in how to erase unused disk space on my hard drive.
Also, how do perform a safe wipe of e.g. /dev/sda?
Kind regards,

/G

---

### Post by lupine_nickt on 2006-08-20
"dd if=/dev/random of=/dev/sdXX bs=512" would do the trick, especially if you ran it several times. It would be slooooooooow, however. /dev/zero would be faster (but less secure).

The only way to be absolutely certain that whatever you're trying to wipe can't be recovered, however, is the method involving a hot fire and a big hammer...

xF,

...Nick

---

### Post by qrwe on 2006-08-20
OK, should of course have mentioned I've done that once before and that I'm asking anyway because of the slooooow time! ;-) Any faster way anyone, some smart program or something..
FYI: In Windows (yep, still using it) there's a pretty smart Open Source tool called Eraser (eraser.sourceforge.net) that does the thing, and it handles wiping of unused disk space too. Alas, it's not available for Linux.

/G

---

### Post by lupine_nickt on 2006-08-20
Curiosity killed the cat; a quick dd experiment on my (EIDE) swap partition with /dev/zero, and a bs of 8M, gave me an average write speed of around 16MB/sec. It's all in the block size ;). Mind you, that's still 3 1/2 hours to cover 200GB, which isn't so pretty.

Bearing in mind, though, that my HD was in use at the time, and you're on SATA rather than EIDE, and TBH I think you could get an acceptable speed out of /dev/zero. 

wipe (in the repos) is a program that also does the trick - can't vouch for it's speed, though.

xF,

...Nick

---

### Post by qrwe on 2006-08-22
I'm very delighted with the quick response, however. Thanks very much!

/G

---

