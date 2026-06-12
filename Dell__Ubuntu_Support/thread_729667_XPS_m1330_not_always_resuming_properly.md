---
title: "XPS m1330 not always resuming properly"
date: 2008-03-20
forum: Dell  Ubuntu Support
---

### Post by sdennie on 2008-03-20
I have a Dell XPS m1330 and suspend/resume works every time without fail (even with the nvidia 8400M GS).  However, it sometimes comes back from suspend and sticks on the screen which shows an error while loading the webcam driver (which works regardless of the error) and I'm forced to hit Ctl-Alt-F7 to get to the login prompt.  Has anyone else seen this sort of behavior and know how to fix it?  It's not vital in that it's easy enough to get around but, it would be nice to have the machine come back from suspend and always go straight to the login screen (so I can show off my fancy linux laptop to friends...).

---

### Post by notwen on 2008-03-20
Have you applied any of the fixes shown [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues") on Dell's Linux Wiki?

[This]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure") may or may not be related to your issues.  Browse the known issues affecting the m1330 and look to see if they are affecting your system.  Hope this helps.  =]

---

### Post by sdennie on 2008-03-20
I've used the relevant Dell fixes (and have been very happy with how good that site is in general).  The problem I described is not predictable and I can't even think of any reason for why it would sometimes decide to stay on the non-X tty after resume.  As I said, it's not vital that I fix it (a simple Ctl-Alt-F7 gets me to where I need to be) but, it would be great if someone knew what the problem was.

---

### Post by bbock on 2008-03-21
Hi,

I have the same notebook with the same Nidia GPU. Same issue here. About 1 in every 20 resumes the notebook sticks in text mode and I must switch back to X manually.

best regards
Bernhard

---

### Post by notwen on 2008-03-22
Curious whats your RAM and swap sizes?

---

### Post by sdennie on 2008-03-22
I'm running with 4GB of RAM and 4GB of swap.  But, I don't use hibernate, just suspend.  So it shouldn't be an issue of not having enough swap to store all my memory.

---

### Post by notwen on 2008-03-23
> **vor said:**
> I'm running with 4GB of RAM and 4GB of swap.  But, I don't use hibernate, just suspend.  So it shouldn't be an issue of not having enough swap to store all my memory.

Yeah, I'm clueless.  Even if you were hibernating that amount of RAM/SWAP would be more than sufficient, lol.  Maybe someone w/ more experience in this area will come along.  Best of luck.  =]

---

