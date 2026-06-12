---
title: "Yet another resolution issue"
date: 2006-06-15
forum: Desktop Environments
---

### Post by EvergreyNY on 2006-06-15
So few days ago I get a used computer from my sister's job and decide to give Linux a shot. I download Ubuntu 6.06, install it, and merrily start learning. I realize my screen resolution is set to 1024x768. Not the usual 1600x1200 if been used to using for the past 3 years.

I searched google for solutions and ended up here most of last night trying out the various things that have been posted, but I ended up with no results. The video is the onboard on the SiS 650 chipset in the computer. I figured maybe that was the issue so I installed an old Nvidia GeForce2 MX 200 that I had laying around. I then reinstalled Ubuntu (I don't know how to install new drives and couldn't get the GUI up) and the screen was set to 1600x1200 in the Live demo. Unfortunatly it reverted back to 1024x768 after the install, once again with 1024x768 being the highest setting.

So I know that the video card does infact support 1600x1200 output, I just can't get xorg to aknowledge  it.

---

### Post by EvergreyNY on 2006-06-15
Haha, well I seem to have solved my own problem. I forgot to run dpkg-reconfigure xserver-xorg again after installing the new video card.

---

