---
title: "Another Dual Monitor problem"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by richbiskit on 2007-05-12
Hi all.

I am TRYING to get a second monitor working on my Toshiba Sat Pro L20 but i just don't know what to do!!!  ](*,) 

I am running Kubutu 7.04

The laptop uses an on-board Intel 915 chip using the i810 driver, my external monitor is just an old generic screen that will run 1024x768 at 60Hz

i have looked over so many how to's but they all seem to be for nvidia or ati.

If anyone can post a configured xorg.conf  file or help me through it i would be sooooooooooo greatfull :D

---

### Post by nazgul77 on 2007-06-30
installing the xserer-xorg-video-intel package quickly gets you into clone mode for the second monitor. You can also now change the resolution. Log out and in again to apply the changes (or recklessly by ctrl+alt+backspace)

In a terminal

 *#sudo apt-get install xserer-xorg-video-intel*

---

### Post by richbiskit on 2007-07-01
Many thanks, i will give that a try :D

---

