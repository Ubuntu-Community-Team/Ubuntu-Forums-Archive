---
title: "AlienArena 7.50 error"
date: 2010-12-28
forum: Gaming &amp; Leisure
---

### Post by luks255 on 2010-12-28
Hey there, I recently downloaded Alien Arena 7.50 and tried to compile it. I already have all dependencies installed.
I go to alienarena's folder and tried "sudo make clean; sudo make; sudo make install" and its got an error. same with source folder.

Output:

```
lucas@stoews-desktop:~$ cd ~/alienarena-7.50
lucas@stoews-desktop:~/alienarena-7.50$ sudo make
make: *** No targets specified and no makefile found.  Stop.
lucas@stoews-desktop:~/alienarena-7.50$ sudo make install
make: *** No rule to make target `install'.  Stop.
lucas@stoews-desktop:~/alienarena-7.50$ sudo make clean
make: *** No rule to make target `clean'.  Stop.
lucas@stoews-desktop:~/alienarena-7.50$ cd source
lucas@stoews-desktop:~/alienarena-7.50/source$ sudo make clean
make: *** No rule to make target `clean'.  Stop.
lucas@stoews-desktop:~/alienarena-7.50/source$ sudo make
make: *** No targets specified and no makefile found.  Stop.
lucas@stoews-desktop:~/alienarena-7.50/source$ sudo make install
make: *** No rule to make target `install'.  Stop.
lucas@stoews-desktop:~/alienarena-7.50/source$ 

```

Please help?

---

### Post by Hur Dur on 2010-12-28
Did you use ./configure beforehand?

---

### Post by Siph0n on 2010-12-28
Also, I think only make install requires sudo.... ./configure and make do not require it (I don't think).

---

### Post by Hur Dur on 2010-12-28
> **Siph0n said:**
> Also, I think only make install requires sudo.... ./configure and make do not require it (I don't think).

Doesn't ./configure create the makefile?

---

### Post by thatguruguy on 2010-12-28
You may want to run the .deb file from playdeb.net, instead. You can get it [here]("http://www.playdeb.net/software/Alien%20Arena").

---

### Post by luks255 on 2010-12-29
Allright, i solved it. When I ran ./configure, it said something about an ode file, which didn't exist. So I asked help to a friend o' mine. Heres the page where i dled it with instructions:

[http://bugs.launchpad.net/ubuntu/+source/ode/+bug/472024](http://bugs.launchpad.net/ubuntu/+source/ode/+bug/472024)

In the last comment.

Then I compiled it. Installed it.

Now I have another problem:

When I open AlienArena, It shows a black screen and that's it. It keeps there.
This is the terminal output:

```
using /root/.codered/arena for writing
execing default.cfg
Could not exec config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Initializing OpenGL display
...setting mode 3: 1024 768
Error couldn't open the X display
ref_gl::R_SetMode() - invalid mode
Initializing OpenGL display
...setting mode 3: 1024 768
Error couldn't open the X display
ref_gl::R_SetMode() - could not revert to safe mode
ref_gl::R_Init() - could not R_SetMode()

ODE INTERNAL ERROR 1: assertion "g_bODEInitialized" failed in dCloseODE() [odeinit.cpp]
Received signal 6, exiting...
root@stoews-desktop:/home/lucas/alienarena-7.50/source#
```PD: Gonna try with the PlayDeb Package :)

EDIT: Also I meet all requirements and have the latest driver for my video card.
EDIT2: Also I want to solve my problem here too, apart from taking the easy exit, Just for those who can't use .deb packages. I'm going to make a guide with this.
EDIT3!!: I went to the PlayDeb package page, and 4 9.10 its just 7.33, i want 7.50 :/

---

### Post by Irritant on 2010-12-29
Looks like you are having a problem with the game's default resolution of 1024x768.  Does your xconfig support it?

---

