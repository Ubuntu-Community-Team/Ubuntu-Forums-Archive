---
title: "Open Arena Problems-Help with booting it up"
date: 2007-05-26
forum: Gaming &amp; Leisure
---

### Post by bokchoi on 2007-05-26
Hey guys.

I recently got Ubuntu and decided to look into some open-source games that would work with it. I came across Open Arena and installed it through the Add/Remove Program dealy, and seemed to install just fine after the download. I went to the Games menu to open it up.  When I click it, my screen turns black for a moment like its going to load up, then it reverts back to my desktop. It seems like it's crashing back to the desktop, and I've read almost every possible guide on how to fix it, and I've already tinstalled linopenal0a and everything so basically I have no idea what to do.

If you guys could help at all it would be freaking great. Thanks in advance.

---

### Post by DoktorSeven on 2007-05-26
Do you have 3d drivers installed?

Try running **openarena** from a terminal and see what it says...

---

### Post by bokchoi on 2007-05-26
> ***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

That's what it said when I try to run it through the terminal.

---

### Post by myoungf1 on 2007-05-26
You definately don't have 3d drivers installed so you don't have direct rendering which open arena needs to run properly.  What sort of graphics card do you have?

---

### Post by bokchoi on 2007-05-26
I see. I have an ATI Radeon x1300.

EDIT: If anyone can direct me to a site showing me how to install 3D drivers for an ATI Card on Ubuntu that would be much appreciated.

EDIT AGAIN: Nevermind, I found the problem. I had to enable restricted drivers. Sorry for such a bothersome question and thanks to everyone who tried to help.

---

