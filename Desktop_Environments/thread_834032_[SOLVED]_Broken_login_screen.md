---
title: "[SOLVED] Broken login screen"
date: 2008-06-19
forum: Desktop Environments
---

### Post by pumbani on 2008-06-19
Hi there,

I just upgraded my memory from 1 GB to 4 GB and suddenly my x login screen no longer comes up. X itself starts but the little clock thingy just keeps going around and around and doesn't actually bring up the login screen. I can go to a terminal and that still works. I'm running 6.06 on a core duo HP nx9420 laptop. Any ideas what might be wrong?

Thanks.

---

### Post by lut4rp on 2008-06-19
When its doing the "clock thingy", try ctrl+alt+F1. Can you spot some error messages?

---

### Post by pumbani on 2008-06-19
Sorry for being technical with "clock thingy" ;-). I just mean the little thing that shows the computer is busy. In Windows it'd be an hourglass... I can go to the terminal (ctrl+alt+F1) and there don't seem to be any error messages. I killed gdm and then tried doing a "startx" from the terminal and that wasn't happy either. Further investigation seems to show that the whole computer is running way slower now in ubuntu with the new memory. It still works fine in Windows though (groan).

---

### Post by argail1980 on 2008-06-19
have you tried to 

```
dpkg-reconfigure --all
``` THIS WILL TAKE A LONG TIME

maybe there is some part of the kernel that needs to be configured for the new RAM...

There's another possibility: your new RAM could be corrupted, so that gdm unfortunately writes to an address where the damage is...

---

### Post by pumbani on 2008-06-19
Cool beans, I'll try that and let you know how it goes. I'll go grab some lunch so long...

---

### Post by pumbani on 2008-06-19
It's still unhappy :-(. dpkg-reconfigure seemed to hang when it was auto-detecting the screen bit - I couldn't even get to another terminal screen. Perhaps I should restart and tell it not to do that... Groan.

---

### Post by pumbani on 2008-06-20
Okay, I have solved the problem (with a little help from my friend google). It turns out that even though 4GB's of memory should be addressable on a 32bit machine, something to do with the spec means that some of that address space is reserved for other things. And apparently Ubuntu didn't know about that. So adding mem=3G to the grub boot line fixed the problem.

---

