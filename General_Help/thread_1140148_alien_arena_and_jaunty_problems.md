---
title: "alien arena and jaunty problems"
date: 2009-04-27
forum: General Help
---

### Post by liferules on 2009-04-27
I just upgraded from Intrepid to Jaunty and the upgrade was fairly seemless. I am having issues with Alien Arena and right now it does not run at all. I have tried thew version in the repositories and the newest version from their web site but I get the same results from the terminal:


-------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  31
  Current serial number in output stream:  34

I am assuming that it is an issue with either a differnt Xwindows version or CFG file conflict. Any suggestions?

---

### Post by huntzire on 2009-04-27
> **liferules said:**
> I just upgraded from Intrepid to Jaunty and the upgrade was fairly seemless. I am having issues with Alien Arena and right now it does not run at all. I have tried thew version in the repositories and the newest version from their web site but I get the same results from the terminal:


-------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  31
  Current serial number in output stream:  34

I am assuming that it is an issue with either a differnt Xwindows version or CFG file conflict. Any suggestions?


Instresting, I want you to get a few bits of information for me, first 

run command glxinfo and paste that in "```
 
``` tags"

Also are your drivers up to date? Is it Nvidia, ATI, opensource?

If you want to find update drivers check the company web site if you need more asst just post it =)

also did you complie a SVN or not? If you didnt you might want to give it ago and ill walk you though that process.

1. sudo apt-get install subversion.
2. sudo apt-get build-dep alienarena
3. mkdir aasource
4. cd aasource
5. svn co svn://svn.icculus.org/alienarena/trunk (this may take abit)
6. cd trunk
7. cd source
8. make
9. cd release mv crx.sdl  to the top level of your aasource/trunk area, so in the truck directory,

once there go ahead and run it from terminal

if that works then you probrlay didnt have some dependency that was required, but most likely I'm suspecting you need to update your drivers.

---

### Post by liferules on 2009-05-05
Thanks huntzire,

It was the Nvidia drivers. I forgot that they are not installed by default. As soon as I installed them Alien Arena worked just fine. Thanks for the brain nudge.

---

