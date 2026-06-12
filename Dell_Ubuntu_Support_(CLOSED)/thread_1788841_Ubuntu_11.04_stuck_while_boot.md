---
title: "Ubuntu 11.04 stuck while boot"
date: 2011-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rookie_11.04 on 2011-06-23
Hello everyone,

I am using a DELL XPS L501X having a NVIDIA graphic card of 1 GB.
I am new to ubuntu. 

I installed Ubuntu 10.10 and then by the update pop up i updated it to 11.04. But sooner i realised that unity is not working on my system. So i started reading some posts and did something.

As a result, now ubuntu does not boot even. I think i crashed the X window system. While booting it goes to the text mode with [OK] signs on the right like old linux distros.

It stops at this line --- Starting AppArmor profiles

Then the cursor is unresponsive and makes everything non functional.

Please help me out how to get this fixed.

---

### Post by Beacon11 on 2011-06-23
> **rookie_11.04 said:**
> ... So i started reading some posts and did something.

You gotta help us help you, man. Mind explaining what you did?

---

### Post by Je Et on 2011-06-23
I noticed one word in your post that tells me what your problem is, **NVIDIA**. **treasonvoice** posted in this thread the answer that solved m problem. The thread is [here]("http://ubuntuforums.org/showthread.php?t=1728379"). Now I'm not a power user, but this is how I did it. You MUST be in **low-graphics** mode. I have on-board graphics plus Nvidia card, so I went into bios and changed to on-board, and then changed my monitor. You can also try booting in recovery mode, then low graphics mode. The reason I had to use on-board was because I was freezing in everything. Hope this help.

Je Et

---

### Post by Beacon11 on 2011-06-23
Not sure that's the same issue Je Et. Rookie, I would also like to know what you mean by "unity is not working on my system."

---

### Post by rookie_11.04 on 2011-06-23
It gave an error msg after complete install that harware is not supporting Unity and you have to switch back to Ubuntu Classic. So i switched to Ubuntu classic. While operating in classic i installed the recommended driver of NVIDIA. But still it showed that it has been installed but not functional or operative.

Moreover when i boot from recovery mode it boots into ubuntu classic fine. I dont understand this that if the installation is corrupted then how can recovery mode is running fine? Does recovery mode take resources from somewhere else?

---

### Post by rookie_11.04 on 2011-06-24
plz tell me if there is any more relevant information that i shud provide

---

### Post by Beacon11 on 2011-06-24
Did you install the driver from repos or from the NVIDIA website? Have you tried uninstalling it?

---

### Post by rookie_11.04 on 2011-06-24
i installed the driver suggested by the repos. no i did not uninstall it. 

I think that i need to reinstall the x-window system again. maybe ive corrupted it totally

---

### Post by Beacon11 on 2011-06-24
I would try uninstalling the NVIDIA driver first.

---

### Post by rookie_11.04 on 2011-06-24
hey got the x-server back..... went to recovery mode and just loaded the old graphics settings.....

---

