---
title: "Keyboard does not work when inside X windows"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Belathor on 2006-07-20
Hi!

As the thread title says, I can't use my keyboard inside of X windows. I can use it to log in on the GDM screen, but once I do that the keyboard becomes useless.

This just started happening yesterday and it is definitely frustrating. I am running AIGLX so that may be the problem. Yet, I'm not sure how to disable it like I can disable XGL on my desktop.

Basically the only thing I can do with my computer is use the command line by pressing ctrl+alt F1.

Any help would be appreciated!

Thanks!

---

### Post by TravisNewman on 2006-07-20
I'm not familiar with AIGLX, so that could be a possibility. However, I've had the same problem when using a KVM switch. Do you have a KVM? If so, try to bypass the KVM and plug directly into your PC.

---

### Post by Belathor on 2006-07-20
Unfortunately, no. I forgot to mention that my computer is an IBM laptop. Thanks for the reply though.

---

### Post by Belathor on 2006-07-24
I've discovered that my keyboard does work. However, it takes about a second of continually pressing down each key in order for a stroke to be recognized. I feel as if I'm using some kind of ancient typewriter. Windows works fine, so I know it is not my keyboard.

---

### Post by Belathor on 2006-07-24
Does anyone know how I could disable aiglx temporarily?

thanks

---

### Post by richbarna on 2006-07-24
> **Belathor said:**
> Does anyone know how I could disable aiglx temporarily?

thanks

Try reconfiguring the keyboard first.

Go to the console "Ctrl + F1" and type 
> sudo dpkg-reconfigure xserver-xorg
just go through the instructions until you get to keyboard and make sure everything is how it should be.

---

