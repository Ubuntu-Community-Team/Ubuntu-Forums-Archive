---
title: "Where in unix history is frel?"
date: 2009-04-01
forum: General Help
---

### Post by LawC on 2009-04-01
Hey everyone:
   I'm still fairly new to this Linux thing. I'm totally in love with it. I've already converted 2 other friends. I've enjoyed learning abit about what Linux stands for (freedom) and where it comes from (unix). One day I was playing around on bash, when I suddenly remembered using some kinda unix system in high school, back in the early 90's. I think it was a unisys icon (?)perhaps running Qunix (?). Since bash is bourne again shell from unix I thought I could use the one and only command I remember from high school: "frel" for "file release". I was sorta surprised when the command was not recognized. I also read that there other shells available; but bash is the best mix of best.  I don't need to use frel, but I just wondered where in history is it?
   If any one would like to share some Unix history lessons with me, I'd love to hear them, so I can begin to piece this puzzle in my head together.
  Perhaps someone knows a good source to learn some history. I hate reading books, so I'm looking for something kinda short and sweet. Would installing LFS (linux from scratch) help? I'm beginning c/c++ programming, and I'm starting to feel a need to learn more about the system. I feel xserver (which I only know as an option in the sessions menu) is a big part of linux, but I don't understand how it fits into the picture...

Thanks for reading and if you have any info/history you'd be willing to share, I'd love to read it!

---

### Post by 3Miro on 2009-04-01
Other than bash I know about c-shell. Type csh and you will be in a different shell, maybe it will support your commands.

I cannot help with detailed history of Linux and different components, what I know is that Unix was accidentally created and was banned under the antitrust laws at the time (it was so superior to everything else). There were different versions of it circling around, but it could never reach the masses. It couldn't be "sold" like MacOS or DOS at the time. Then Linux was created semi-accidentally and grew in itself, using the unix ideas, and now Linux is the most sophisticated OS.

Linux is actually a very small part of the system, it is the kernel. The thing that runs all other things. The kernel functions are things like memory management, scheduling the CPU between different processes, HD and general device access (and hence security) and other "basic" tasks. The X server is the core of the visual environment. The first X servers created for Unix predate Linux and even windows 1 (that is in the 80s, before win95 and before win 3.1). I think all that the X server can do is draw pictures on the screen using whatever video card one might have. Then comes the desktop environment and there are may flavors: Gnome (Ubuntu default) and the big competitor KDE, XFE and others. Gnome and KDE aim at complexity and many many features, while some of the others aim at simplicity and light weight. You pick whichever one you like. The desktop comes with a hole bundle of common applications (KDE and Gnome aim to provide a complete set of apps to do all your needs). You can run apps created for one desktop on another, but you will have to load more libraries (basically the other desktops' libraries) and that takes time (initially) and RAM. Sometimes there are stability issues. In general under a desktop environment, you should try to run as many "native" apps as possible, you will get maximum performance and stability.

---

