---
title: "Hardy Heron &amp; Intel 945GM Dual Monitor"
date: 2008-07-05
forum: Desktop Environments
---

### Post by joaoxxx on 2008-07-05
Hey everyone,

I've read almost all FAQs on this subject and I just cannot solve this problem. I've been using Ubuntu since Gutsy (dual boot w/ XP), but Hardy Heron really made things difficult for me. For instance, when starting up for the first time, some fonts are too big, and the resolution is under the 1280x800 it should be in (worse in Xubuntu, where all fonts are big and I just can't do anything).

I've tried to solve this with the display settings, and also by activating a minor 'screens resolution' option under 'Other' in Apps. I've messed around a little bit with xorg.conf but the best I was able to do was 'repair' my resolution and then trying 'cloned windows' mode. Even when that happens, my PC is hooked up (S-Video to SCART) to a CRT Tv in Pal, so the image is black & white. This goes all the way to 7.04 and outwards to Fedora, which has a 'dual monitor' GUI that just doesn't work.

My question is, 1, is there a simpler interface for dual monitors to be expected in 8.10? 2, is there hope AT ALL with my video card? This is important to me as I usually watch a lot of movies and shows in my TV via S-Video hookup. 3, if there is a solution, can it not go through xorg.conf? I'm an entry-level user and I just don't know how to do code.

Thanks everyone, I'll post screens and paste code when requested.

---

### Post by overdrank on 2008-07-06
HI and welcome, you may look here
[http://ubuntuforums.org/showthread.php?t=849994](http://ubuntuforums.org/showthread.php?t=849994)
I myself have not tried it and have not had success with dual screens with my laptop.

---

### Post by ramaswamyps on 2008-07-06
thanks for reply.
i am not yet looking for dual screen.
ihave installed this in my desktop p4 845 motherboard.
i have various grub problems.
this is a multiboot computer.
any change in any other partitions next boot grub gives invalid device string error.
after this repair only i will investigate the screen problems.:)

---

### Post by overdrank on 2008-07-06
> **ramaswamyps said:**
> thanks for reply.
i am not yet looking for dual screen.
ihave installed this in my desktop p4 845 motherboard.
i have various grub problems.
this is a multiboot computer.
any change in any other partitions next boot grub gives invalid device string error.
after this repair only i will investigate the screen problems.:)

:confused: are you replying to my post?

---

### Post by joaoxxx on 2008-07-06
Sorry, no can do. I can't "make install" the tar.gzs you referred to, and besides, I use i810 already. I hope the next Ubuntu comes with some form of automatic detection of S-Video/VGA/DVI connections, because otherwise you just have to know how to 'hard code' the devices into your display configuration. I also wonder if this isn't a prime question for teachers and students everywhere, who have to hook up their little ubuntus to datashows for their classes.

---

### Post by daparic on 2008-10-10
hello,

I have a Lenovo T60 with Intel 945GM dual output. After several days trying to setup a working configuration file in xorg, I found another way which is easier and also more flexible. With Ubunto 8.04 you should already have xrandr support in X, so you just type (it works also as normal user)

"xrandr -q" you should get notification of detected monitors that are plugged to your computer. Mine is LVDS for the laptop display and VGA for the external monitor. then, I type

"xrandr --output VGA --auto" then I get dual screen on my external monitor, then I type

"xrandr --output VGA --left-of LVDS", then VOILA, I get extended monitor (provided that the external is on the left of my laptop".

you can disable external monitor by "xrandr --output VGA --off"

you can play around with some options to improve the situation in your case. Personally, I put those commands in a single batch file, then attached a personalized command in my Panel, so I can switch on or off the dual display on the fly (no X restart needed)

hope this helps. It took like a week for me to find the working solution.

---

### Post by xv1700 on 2008-11-17
I have just tried setting up dual monitor on Intrepid on a Lenovo T60 with an Intel 945 driver. My first port of call was the standard "Screen Resolution" application. Initially I was getting mirrored screens and unchecking the "Mirror Screens" had no effect at all, "Detect displays" did nothing. I read all the articles about modifying xorg.conf and thought "looks horrid" so I ran "xrandr --output VGA --off". The VGA monitor went off, then I tried the "Screen resolution" programme again and BINGO!!! No file changes, no messing around and I have full dual monitor support.

Thanks for the top tips.

---

