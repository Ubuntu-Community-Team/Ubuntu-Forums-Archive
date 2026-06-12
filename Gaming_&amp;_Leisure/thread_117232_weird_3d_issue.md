---
title: "weird 3d issue"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by hone on 2006-01-14
under /proc/driver/nvidia/agp/status when it is enabled with 8x and AGPGART as the driver I get 75 fps in glxgears -printfps and when I don't have it enabled and the cpu pegs to 100% when I run it with the status showing disabled I get 6k+.  I feel like I can't use my vid card to its full potential.  I should be getting better frames in all my games.  Like it's capped @ 75 in quake 3 and in quake 4 things are chopping @ 8x6 with medium settings.  Warcraft III wont' even play at smooth frame rates even w/ the -opengl switch.

I have the following hardware:
AMD Athlon 64 x2 3800+
512 mb of 2x256 dual channel pc3200 OCZ
Nvidia GeForce 6800GT 256 mb
and a ASRock 939Dual-Sata2

I was wondering if anyone can off any advice.

---

### Post by Mr_Grieves on 2006-01-14
I have the same graphics card as you, and I am not experiencing these problems.
Do you have the latest Nvidia driver installed?

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by hone on 2006-01-14
I have the latest one in the repository, so 7667 but not the latest 8xxx I found on the nvidia site.  I'm not really sure how to go about this one.  I've never really had problems with my nvidia cards in the past.  I just replaced my mobo and cpu from a nf2 board w/ an athlon xp 1700+ to my asrock and 3800+ last week.  The videocard worked fine before.  Is it because I'm using a smp kernel and dual core?  Do they give issues to nvidia drivers?  I did some researching and realized nvagp doesn't support my uli board, so I have to use agpgart.  I remember agpgart being significantly slower than nvagp in the past, maybe that's it, but then there's no fix?

---

### Post by Mr_Grieves on 2006-01-14
Seems others in this forum aswell are having problems with SMP and graphics.. for some though it seems to be working good.
I have myself no idea.. try running without SMP and see if you still get the problem.

[http://www.ubuntuforums.org/showthread.php?t=114768](http://www.ubuntuforums.org/showthread.php?t=114768)

---

