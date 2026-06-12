---
title: "help updating the kernel"
date: 2009-04-07
forum: General Help
---

### Post by super-sauce on 2009-04-07
Okay so I'm on ubuntu 8.10 using 2.6.27-11-generic on my athlon 64 x2 4200+ and would like to know if I should switch from the generic kernel to the amd k7-smp kernel.  Sometimes Ubuntu will lag out and I'm hoping that switching form the generic to the actual k7-smp kernel will help.  For example when I'm playing a video with Totem it will sometimes go to 60%+ cpu usage, and if I go on the net while watching Star Trek the video will sometimes slow to a crawl.  All I really need to know is the terminal command to install the new kernel (yeah I forgot it).  Can anyone help me out?:KS :KS

---

### Post by 3Miro on 2009-04-07
I am using AMD Athlon 64 X2 and I have no trouble with the generic kernel. The version that you are talking about, is it in the repositories or somewhere else. If it is in the repos, you can just download it and give it a try, otherwise it is probably too much trouble and it may be incompatible (or not fully compatible) with Ubuntu.

Video sounds like a video driver issue.

---

### Post by nebileix on 2009-04-07
```
sudo apt-get install linux-*
```

or use synaptic to do the installation.

---

