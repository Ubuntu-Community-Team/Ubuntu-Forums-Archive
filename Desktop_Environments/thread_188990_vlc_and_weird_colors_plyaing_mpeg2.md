---
title: "vlc and weird colors plyaing mpeg2"
date: 2006-06-04
forum: Desktop Environments
---

### Post by tonny on 2006-06-04
Hi

I have som problems playing video in vlc. When playing high definition .ts mpeg2 video files and other mpeg2 video clips, the color somehow gets distorted. It looks as the color is displaced compared to the contrasts (black / white image).

This does not ocure in mplayer, but mplayer cannot handle .ts files and plays theese in a framerate of 3 - 4 frames per second and eventualle crashes with some erroe saying "to many packets in videoframe" or something like that.

please take a look at the attached screenshot.

I run the newest nvidia driver, and uses the xgl server and compiz composite manager. Keep in mind vlc plays divx / xvid clips fine without theese color distortions.

---

### Post by Deus42 on 2006-09-05
I have this problem on two systems when playing XVID, both of which are running XGL and Compiz

One system is running AMD64 with an NVIDIA card(using nvidia drivers), the other is an intel laptop with a ATI firegl (using fglrx drivers) card.

on the ATI card all I did was uncheck the "Deinterlace" option and it was fine, but I have yet to fix the problem on my AMD64 system.

One other thing that I thought was very interesting was that if I disabled the extmod xorg module, it also fixed the problem on the computer with the firegl card.

---

