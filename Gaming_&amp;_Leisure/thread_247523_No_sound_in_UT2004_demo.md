---
title: "No sound in UT2004 demo"
date: 2006-08-30
forum: Gaming &amp; Leisure
---

### Post by fatsheep on 2006-08-30
I always used to get sound on the UT2004 demo but I fired it up today and nothing's coming out of my speakers. :confused: 

I tried running it in the terminal and although the sound still didn't work I picked up an interesting clue:

> 
fatsheep@fatsheep:~$ ./ut2004
**open /dev/[sound/]dsp: Device or resource busy**


Any ideas?

---

### Post by tribaal on 2006-08-30
Hum I canoot explain *why* exactly, but I had the same kind of error with quake3.

Try typing the following in a terminal:

```
sudo killall esd
```

This will kill the ESD deamon which is a sound demon (from what I understand) that locks the sound device (/dev/dsp).

Worked for me...
Hope this helps.

- trib'

---

### Post by DoktorSeven on 2006-08-30
Close all programs that make sound then

killall esd
(or killall artsd if you're using KDE)

then try again.  

This should really be some sort of sticky here, or something.  "ATTN: Sound not working, try this" or something.  Same with slow or no 3d.  Way too many questions asked about these two things.

---

### Post by tribaal on 2006-08-31
I agree, this solution shoud appear in a sticky somewhere. I think the solution is the same for "no sound in flash", but then you have to restart firefox.

Is there another sound demon we could use that would "just work"? Esd seems to be giving headaches to everyone...

- trib'

---

### Post by fatsheep on 2006-08-31
Thanks for the tip guys, either restarting or running that command fixes the problem.  

> 
Is there another sound demon we could use that would "just work"? 


I'll just hope for the best in edgy. ;)

---

