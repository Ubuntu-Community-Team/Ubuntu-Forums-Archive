---
title: "dreamchess has no chessboard!"
date: 2011-06-25
forum: Gaming &amp; Leisure
---

### Post by odnesium on 2011-06-25
After a fresh install of ubuntu 10.04, Dreamchess no longer has a chessboard.  There are pieces and one big square where the board should be but none of the checkered squares for game play. It may go without saying the pieces will not move.  I have tried  uninstalling and reinstalling. no change. There is no proprietary video hardware on my machine.  Any suggestions would be great. Thanks in advance

---

### Post by haqking on 2011-06-25
> **odnesium said:**
> After a fresh install of ubuntu 10.04, Dreamchess no longer has a chessboard.  There are pieces and one big square where the board should be but none of the checkered squares for game play. It may go without saying the pieces will not move.  I have tried  uninstalling and reinstalling. no change. There is no proprietary video hardware on my machine.  Any suggestions would be great. Thanks in advance


try here

[http://packages.ubuntu.com/lucid/dreamchess](http://packages.ubuntu.com/lucid/dreamchess)

---

### Post by odnesium on 2011-06-25
Thanks for the quick reply.  I followed the link but I'm afraid I don't know what to do once I'm there. Lots of useful package's there I'm sure. I don't understand the nature of my problem well enough to know what to download. It may be worth adding that Brutalchess has the exact same problem.

---

### Post by brencameron on 2011-06-26
Are you using 32-bit or 64-bit? I'm asking because on 32-bit, dreamchess had a rotating board when I tried to play it(10.04/10.10), while on 64-bit, it was perfectly fine.

EDIT: ..... and I just re-installed it now. On 64-bit, Mint 11 (Ubuntu 11.04). It's rotating. I guess I don't have a good solution for you. Sorry :(

---

### Post by odnesium on 2011-06-26
Thanks anyway. For the record I'm using 32bit ubuntu on a 64bit processor.  have been searching the internet everyday for a week to find a solution.  So far I have not found any reference to anything even similar.  Very frustrating to say the least.

---

### Post by haqking on 2011-06-26
> **odnesium said:**
> Thanks anyway. For the record I'm using 32bit ubuntu on a 64bit processor.  have been searching the internet everyday for a week to find a solution.  So far I have not found any reference to anything even similar.  Very frustrating to say the least.

so using the link i posted [http://packages.ubuntu.com/lucid/dreamchess](http://packages.ubuntu.com/lucid/dreamchess)

at the bottom you will see download dreamchess.

choose your architecture, which in you case is the i386 as you are running 32 bit and ti will list a page with mirrors which are links to servers where the file is, choose one closest to you (north america, europe etc)

then it was download a file with .deb on the end.  This a packaged instal file for dreamchess bit like a .exe in windows.

double click it and it will install hopefully repairing your install if there is an issue.

this can also be done at terminal through repos and in synaptic package manager.

you can also from terminal

sudo apt-get update

sudo apt-get install dreamchess

basically i am saying reinstall with this .deb or from repos

other than that it looks like some kind of graphics issue.

do you have 3d hardware ? what drivers does it use ? do other 3d enabled software work ok ?

---

### Post by odnesium on 2011-06-27
Now we're getting somewhere. No go on the reinstall with .deb. Still no Squares. I suspect your onto something with the 3d graphics.  I tried to run Flightgear and not only did it not work, but it completely locked up my machine.  Ive been using linux (on a different tower) for about a year now and thats never happened.  Gave me flashbacks from the dark days when I used Windows or rather when Windows used me.

 lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Another two hours of internet searching has me no closer to understanding whether or not this device supports 3d and if so how to enable it/install the proper drivers.  On past machines it's always just worked leaving me happily ignorant. system/admin/hardware drivers shows no proprietary hardware.  I am all about figuring out these kinds of things for myself but I could really use some help on this one.  I am stumped. All input is welcome.

---

### Post by odnesium on 2011-06-29
3-d is enabled and driver is up to date.  Anyone got an idea?
glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2

./compiz-check
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX
At least one check had to be skipped:
 Error: openchrome driver in use

sudo apt-get install xserver-xorg-video-openchrome

---

### Post by odnesium on 2011-07-17
ok well i couldnt find what i was looking for so i had to install a different video card.  Not the answer i was looking for but it works. poorly solved.  :(

---

