---
title: "Monitor / video card problems"
date: 2009-04-24
forum: General Help
---

### Post by Giakki on 2009-04-24
Hi,
I'm a new Ubuntu user. I got an issue with my monitor: since the installation of ubuntu 8.04 at times my monitor turns black until I turn it off and on again.
It also randomly modifies its brightness, or shows weird characters in the osd.
If I boot on windows everything's ok... I tried upgrading to 8.10 and 9.04 but the broblem still persists.

My specs are:
LG Flatron w2234s
Nvidia 8600 gt
Intel core duo

Thanks in advance! :)

---

### Post by Bender2k14 on 2009-04-24
Do you know if you are using the latest proprietary Nvidia driver? (I am not positive about this in 8.04, but) in 8.10 and 9.04, you can view what Nvidia driver you are using (if any) and/or begin using an Nvidia driver by going to System->Administration->Hardware Drivers.

What does the Hardware Drivers window say about your current driver? Try changing to the newest Nvidia driver. Does that help?

---

### Post by Giakki on 2009-04-24
Thanks,
Yes, i'm using nvidia drivers version 180

---

### Post by Almighty on 2009-04-24
Does this happen when the PC goes to sleep or standby? I remember having this issue a while back.

---

### Post by Giakki on 2009-04-24
Nope, it happens randomly when i'm using it, like every 30 seconds...
I looked everywhere and i didnt find anyone with the same problem...

---

### Post by Garric on 2009-04-24
Hi there, I had the pretty much the same problem yesterday - updated the nvidia driver to 180 from 177 and found that when i rebooted that i had absolutely no picture at all. Changed back to 177 and it worked perfectly.

Long story short i updated to 9.04 this afternoon and found that the only nvidia drivers available were 180 and 173, had the same result as before with 180 and am about to try 173.

For the record i am using a nvidia 9500GT (xfx) with which i've had no other problems

---

### Post by Giakki on 2009-04-25
Thanks, now it works properly!
It was that simple :)

---

