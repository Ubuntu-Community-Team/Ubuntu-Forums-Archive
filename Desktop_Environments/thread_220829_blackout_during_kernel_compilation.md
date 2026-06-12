---
title: "blackout during kernel compilation"
date: 2006-07-22
forum: Desktop Environments
---

### Post by reckless2k2 on 2006-07-22
I had a blackout last night during the final step of my kernel compilation:

sudo make-kpkg ..........

My question is whether I have to start the whole process over again?

---

### Post by tturrisi on 2006-07-22
> **reckless2k2 said:**
> I had a blackout last night during the final step of my kernel compilation:

sudo make-kpkg ..........

My question is whether I have to start the whole process over again?
common sense says compilation stops when the power to the comp is shut off.
fyi - a balckout is when the power goes off and stays off for a while.  A brown out is when the power goes off and then back on in a few seconds.  A power surge occurs when the power goes back on after a black out or a brown out.

If is a laptop or if desktop plugged into a battery backup then no worries.

---

### Post by reckless2k2 on 2006-07-22
I appreciate the response. I do know the difference between a brownout and a blackout. I'm just tyring to find out if I have to start back at make oldconfig or make menuconfig or if I can jump right back to make kpkg? 
Thanks.

---

### Post by matthew on 2006-07-22
You can jump in right after the last fully completed command. It sounds like in this case you just pick up at make kpkg.

---

