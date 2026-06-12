---
title: "Various SEGFAULT errors"
date: 2009-08-16
forum: Desktop Environments
---

### Post by csmgj on 2009-08-16
It started with internet browsers closing. Then I learned if I started things in terminals, they would give me errors. Well, I had various internet browsers SEGFAULT, various video games (TORCS for one), Add Remove program. It's driving me nuts. Is it a memory problem? Video? What do I do to trouble shoot further?

I'm running  Ubuntu 8.04 - the Hardy Heron - released in April 2008 on a Lenovo T61 Think Pad.

---

### Post by csmgj on 2009-08-16
Aug 16 15:06:19 marty-laptop kernel: [ 2250.550035] gnome-app-insta[9138]: segfault at 00f6a4f4 eip 08086bf0 esp bf85c790 error 4
Aug 16 15:07:21 marty-laptop kernel: [ 2312.252743] gnome-app-insta[9208]: segfault at 003a2a14 eip 080f3d1a esp bf8acb90 error 4

These are my latest errors from trying to run the add remove app. Wonder what 'error 4' is.

---

### Post by ajgreeny on 2009-08-16
Try purging gnome-app-install and then reinstalling it with synaptic or apt-get.  It appears that that application is causing the segfault.

The removal will also take three other applications with it (ubuntu-desktop, ubufox and apturl on my machine) but you should be able to reinstall those again as well afterwards.

---

### Post by csmgj on 2009-08-16
Kinda reminds me of the universal fix for windows XP, REINSTALL! 

I'd try that, (and might eventually do that to prove that is not the issue), but it doesn't address the fact that other applications are SEGFAULTing. As for reinstalling, it would make more sense to reinstall Ubuntu itself. I hope to avoid that though. (at least until I can get home to wired high speed internet). Seems this problem has been plaguing me ever since I installed Ubuntu on this machine. 

Therefore I think it's a problem with the OS or the machine (or drivers related to the machine). Anyone else running this version of Ubuntu on a T61?

Even still, thanks for the reply :)

---

### Post by csmgj on 2009-08-24
Well, actually it's Firefox that segfaults the most. But reinstalling individual programs doesn't seem to be the answer if I'm having that problem with multiple applications. Anyone have any idea how I might see if hardware or drivers have anything to do with my problems? 

As for reinstalling, I considered I might try another distro to see if it it gives me problems. Given that, which distro might you suggest?

---

### Post by csmgj on 2009-09-15
Well, I downloaded Linux Mint. For some reason I was unable to install it, but was able to run it off the CD. And even on the CD, Firefox STILL segfaulted. Since neither Vista or Linux seem to run right on this Lenovo pile of overpriced crap, could it be the machine itself? If so, can you recommend tests?

---

### Post by csmgj on 2009-09-16
Wow, after a year of problems with this over priced laptop, looks like I found the problem. It isn't Vista, it isn't Ubuntu, it was the memory. If anyone else finds this, or has these problems, you can run the memory test when booting linux. It's generally one of the boot options under GRUB.

---

