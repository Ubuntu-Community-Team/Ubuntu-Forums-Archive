---
title: "Latest Gutsy Updates Hosed Wireless on e1505"
date: 2007-09-22
forum: Dell  Ubuntu Support
---

### Post by mojoguy on 2007-09-22
Just an FYI... the latest Gutsy updates have hosed wireless on my e1505 (purchased with Ubuntu installed).  These were installed on 09/23/07 (or the day before...haven't restarted in a couple days).

Booting off the Gutsy Tribe 5 CD lets me use wireless.

Not sure if anyone else has run into this....

---

### Post by mojoguy on 2007-09-22
The wireless card is unclaimed.  Driver still appears as enabled in restricted drivers, but not used.

---

### Post by basotl on 2007-09-23
I have the same issue with my Inspiron 9300. Intell b/g 2200 wireless card.

Last update fixed some issues and broke this one.

---

### Post by mojoguy on 2007-09-23
Yeah, mine is the intel 3945 wireless.  ;(  

Hopefully this gets fixed soon.

---

### Post by neptho on 2007-09-23
Are/were you using the proprietary ipw3945 driver, or the iwlwifi driver?

I've given up on toying with the iwl driver; ipw3945 has so many problems and thoroughput issues, but I really dislike having to toy with Feisty's older kernel to try to get a recent build of iwlwifi to (not) work - I'm sticking back with Feisty; for some reason the .21+ kernels seem to find a problem with my 6400 and lock it solidly.  .21, .22..but .20 it works fine.  Just without NO_HZ.  :(

---

### Post by mojoguy on 2007-09-23
You know, I think I'm using the iwl driver on my failed Gutsy.  I'll have to reboot into it to check for sure, but I can't do that right now.

---

### Post by basotl on 2007-09-23
I've been busy at work and haven't had a chance to reply about my fix.

That update had an update to the kernel. I just used an older kernel version and it works for me.

Just hit "esc" at the grub load screen and load an older kernel version.

Hopefully this will work for others.

---

### Post by mojoguy on 2007-09-23
Oh, very cool.

One question, if I boot from an older kernel, what do I do with updates?  If I update anything, will the updates somehow get branched so that they won't be for the version with the newer kernel?  Will it ask me to update the kernel again?  

I don't have the correct understanding of how it works to ask the question clearly.

---

### Post by jml on 2007-09-23
A similar problem occurred when one my updates updated the kernal in my Debian box.  It seems that after the update, the new kernal failed to load my wireless module, and it failed to load the headers.  I had to manually download the headers, the wifi module (madwifi in my case,) had to be recreated.  Everything worked fine after that and I was able to use the newer kernal.  The trick that basotl mentioned was how I was able to get back on line to download the stuff I needed.  Hope this helps.

Joe

---

### Post by mojoguy on 2007-09-23
Thanks Basotl...works like a charm.

And Joe, thanks for chiming in.  

My question is thus: I am in no rush right now.  Booting the older kernel is working fine for me.  However, is this the type of problem that will likely get fixed in a future update, or will I have to resort to doing something like Joe did.

---

### Post by basotl on 2007-10-07
This issue was fixed in the last update that I did. The new kernel header did it.

> **mojoguy said:**
> Thanks Basotl...works like a charm.

And Joe, thanks for chiming in.  

My question is thus: I am in no rush right now.  Booting the older kernel is working fine for me.  However, is this the type of problem that will likely get fixed in a future update, or will I have to resort to doing something like Joe did.

---

### Post by michiel.patrick on 2007-10-08
i have an e1405 which i believe is close to the same and gutsy will not even update. I believe this is a problem with a lot of 1405's

---

