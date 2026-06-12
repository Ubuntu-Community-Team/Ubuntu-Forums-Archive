---
title: "experienceing start up problem"
date: 2009-05-21
forum: General Help
---

### Post by Bigneil on 2009-05-21
when i start ubuntu it performs a disk check then displays some errors, but i don't know what to do about it? 

can Any one help?

---

### Post by albinootje on 2009-05-21
Boot from an Ubuntu installation cdrom, use the "live session", and  
run a manual fsck for /dev/sda5 :

```

sudo fsck /dev/sda5

```

---

### Post by Bigneil on 2009-05-21
ok thank you  :)

I had the side of the tower off earlier, i must of accidentally done something to the hard drive.  Doh!!

I tried to boot into xp too, that won't start at all. it want's xp disk to run recovery.

If i fix xp, is it gonna mess up my dual boot

---

### Post by Bigneil on 2009-05-21
I am now able to answer my own question LOL  

all fixed now.   i discovered the root cause of the problem.

I had a dodgy IDE cable that when wiggled must have corrupted data on the hard drive. i think this problem has been there for a while, because i had a very similar problem before, after touching the IDE cable, the hard drive died..   i have nicked the cable from the dvd player/burner until i next pop into the computer shop.

think i should treat myself to brand new cables



SOLVED

---

