---
title: "are there issues with dvd-r support"
date: 2006-07-10
forum: Desktop Environments
---

### Post by stonefeet on 2006-07-10
i ripped a dvd to test if the burning works
shrunk it
4.4gb iso
went to burn tried with k3b and the default burning prog
both said the disc didn't have enough space, i noticed when it was asking for a disc with space on it that it didn't mention dvd-r.

i've searched through the forums and only found 1 thread that has the issue

anyone know about this problem?

---

### Post by Joeb on 2006-07-10
> **stonefeet said:**
> i ripped a dvd to test if the burning works
shrunk it
4.4gb iso
went to burn tried with k3b and the default burning prog
both said the disc didn't have enough space, i noticed when it was asking for a disc with space on it that it didn't mention dvd-r.

i've searched through the forums and only found 1 thread that has the issue

anyone know about this problem?
I've burned dvd-r media, not directly from an iso, though.  However, if I'm not mistaken, an iso is created in the process and then burned.  Regardless, it worked.

That said, the defaults in k3b and the other burning apps are for CDs not DVDs and as such are either 650MB or 700MB.  Are you sure you just didn't forget to change size of the media in the app?  I know it's a stupid question, but usually they're easier to solve. :p 

If that's not it, it's possible that your 4.4gb ISO really is to big to fit on a dvd by the time you multiply it out to actual bytes.  Any chance you can shrink it slightly smaller, say 4.39?

---

### Post by stonefeet on 2006-07-10
> **Joeb said:**
> I've burned dvd-r media, not directly from an iso, though.  However, if I'm not mistaken, an iso is created in the process and then burned.  Regardless, it worked.

That said, the defaults in k3b and the other burning apps are for CDs not DVDs and as such are either 650MB or 700MB.  Are you sure you just didn't forget to change size of the media in the app?  I know it's a stupid question, but usually they're easier to solve. :p 

If that's not it, it's possible that your 4.4gb ISO really is to big to fit on a dvd by the time you multiply it out to actual bytes.  Any chance you can shrink it slightly smaller, say 4.39?

here's what i did
ripped dvd via dvddecryptor in wine
and then used dvdshrink in wine to convert to iso
all set to use 4.7GB blank dvd
then used burn dvd via iso in k3b

i have read that there may be some sort of issue with my dvd burner and its firmware, so i'm going to reinstall windows update firmware then install ubuntu on my 2nd hdd and give it a shot
for now i'll try that and then report back in this thread

it's only the dvd burning issue and the issue with my mouse (scroll wheel and side buttons won't work) once those 2 get sorted
ubuntu for life

---

### Post by stonefeet on 2006-07-10
tick the overburn checkbox

problem solved

---

### Post by orb9220 on 2006-07-10
And the other issue ripping to dvd where sometimes dvd shrink would create a 4.38 intead of 4.35

So in DVD shrink I use custom size in options and lower that to like 4458Mb
insted of the default 4464 and hadn't have any  issues since.

And what is the reason for DVD decrypter to hd first then shrink.

I just rip dvd to hd from shrink. with all the decryption region and compressed ready to burn.

Just curious :-k

---

### Post by stonefeet on 2006-07-11
> **orb9220 said:**
> And the other issue ripping to dvd where sometimes dvd shrink would create a 4.38 intead of 4.35

So in DVD shrink I use custom size in options and lower that to like 4458Mb
insted of the default 4464 and hadn't have any  issues since.

And what is the reason for DVD decrypter to hd first then shrink.

I just rip dvd to hd from shrink. with all the decryption region and compressed ready to burn.

Just curious :-k

i couldn't get dvdshrink to actually read the dvd, it gave me some error that i can't remember off the top of my head
but after some messing around with the winecfg settings i was able to get dvdshrink to read/rip the dvd

---

