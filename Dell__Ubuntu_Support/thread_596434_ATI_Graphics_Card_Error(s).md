---
title: "ATI Graphics Card Error(s)"
date: 2007-10-29
forum: Dell  Ubuntu Support
---

### Post by Daaveh on 2007-10-29
Hi, I finished installing Ubuntu on my Dell PC two days ago, and since then I've been following as many tutorials and forum posts as I could find to try to get Linux to notice my graphics card.

I know I have an ATI card, but I don't know the exact numbers on it. I've reinstalled Ubuntu about 3 times, and I have to run it in safe graphics mode or else I get this error:

```
Failed to start X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?
```

I can start in Safe Graphics mode just fine, and if I try to change my resolution and then restart, I get the same error again. My problem most closely follows this post:
[URL="http://ubuntuforums.org/showthread.php?t=515473&highlight=x+server+error"]http://ubuntuforums.org/showthread.php?t=515473&highlight=x+server+error
[/URL]

When I tried typing in "sudo dpkg-reconfigure -phigh xserver-xorg" and configuring it, I wasn't sure of what to enter for every question, and when I restarted afterwards, I got the error:

```
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":O.O"
after 0 reuests (0 known processed) with 0 events remaining.
```

Can anyone tell me a way to fix this?

---

### Post by Luis Macias on 2007-10-29
Hi, im new to ubuntu, but i had a similiar problem. I installed Ubuntu 7.10 on  a dell laptop with ATI graphics, first time i installed i couldnt use effects and i got errors because i didnd have the driver or something like that. I solved this problem by resintallling ubuntu but this time i connected my laptop by ethernet during all the installation, this time, ubuntu downloaded automatically the audio and graphic drivers when installing and now everything works fine.
Hope this helps

Good luck

---

### Post by Daaveh on 2007-10-29
> Luis Macias  	
Re: ATI Graphics Card Error(s)
Hi, im new to ubuntu, but i had a similiar problem. I installed Ubuntu 7.10 on a dell laptop with ATI graphics, first time i installed i couldnt use effects and i got errors because i didnd have the driver or something like that. I solved this problem by resintallling ubuntu but this time i connected my laptop by ethernet during all the installation, this time, ubuntu downloaded automatically the audio and graphic drivers when installing and now everything works fine.
Hope this helps

Good luck

Hmm... I never even thought of that, although I had my computer connected by ethernet during installation, So I guess that's not it. I had no trouble finding the place to download the drivers for ATI graphics cards [There were many links on the forums], the problem is that Linux isn't detecting my graphics card. It detects "Plug'n Play" for my active screen(In System -> Administration -> Screen and Graphics [Screens]). Under [Graphics Card] it says [i810 Intel integrated Chipset], and under that it says [vesa - Geveric VESA]. When I was running Windows XP[I wrote over it while installing Ubuntu] I had to disable "Plug'n Play" before I could get my new graphics card to work. Possibly this has something to do with why it isn't detecting my card?

[[Thanks for the idea, Luis]]

---

### Post by Luis Macias on 2007-11-15
Sorry i couldnt help, hope u find the solution.

---

