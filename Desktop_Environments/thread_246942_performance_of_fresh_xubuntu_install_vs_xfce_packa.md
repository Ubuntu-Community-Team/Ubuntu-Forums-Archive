---
title: "performance of fresh xubuntu install vs xfce package"
date: 2006-08-30
forum: Desktop Environments
---

### Post by VCSkier on 2006-08-30
i've been using ubuntu for a while, and have been very happy with it, but am interested in increasing performance and responsiveness.  i know xfce is faster, so i think i want to start using it.  should i start with a fresh xubuntu install, or simply install an xfce package?  disk space is not a concern.  if i could insall xfce onto an existing ubuntu installation without any performance differences, what would be the proper package to install?  thanks!

IBM Thinkpad T41 Laptop
1.6 Ghz Pentium M
512 MB Ram
40 GB Internal HDD
120 GB External HDD

---

### Post by Cable on 2006-08-30
I'm not sure about performance differences between installing Xubuntu fresh or installing it alongside Ubuntu, but to install xfce and whatnot you would install ***xubuntu-desktop***.

---

### Post by rejser on 2006-08-30
use aptitude while installing, then if you would like to remove you just type aptitude remove xubuntu-desktop, difference, it will remember dependencies and remove them too.

---

### Post by maniacmusician on 2006-08-30
^yeah, good point. I once installed ubuntu-desktop with apt-get instead of aptitude and without aysiu's tutorial of how to get to a "pure" DE, my system would have been screwed over with the leftovers of gnome. but yeah, "sudo aptitude xubuntu-desktop" should do the trick. 

I use Xubuntu, and in my experience, it has been significantly faster than most DE's i've tried (but not at the expense of seeming bare). If your hardware is properly set up, you can enable the compositing manager to get some nice (but not overdone) eye candy.

---

### Post by Cable on 2006-08-30
Check out [this]("http://www.psychocats.net/ubuntu/xubuntu") page for installation instructions.  If you end up wanting to stay with XFCE and ditch GNOME, look [here]("http://www.psychocats.net/ubuntu/purexfce").  If you end up wanting to stick with GNOME and get rid of XFCE, go [here]("http://www.psychocats.net/ubuntu/puregnome").

---

