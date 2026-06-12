---
title: "[SOLVED] OpenArena"
date: 2008-11-08
forum: Gaming &amp; Leisure
---

### Post by Georgia boy on 2008-11-08
Hi. I've got a quick question(I think) about the OpenArena game. I did the install from the Add/Remove but wound up doing a removal. When I clicked on the game to open it I got a quick black screen then back to the desktop. Is the game not downloading? I had gone to the site for the game before downloading and the last news release was on Oct. 31st. Any ideas as to what is going on? Did I not download the game or is it something else that is downloading instead of the game. :confused: It does look like an interesting game to play.
All advice welcomed.
Thanks
Tom

PS: Have a great weekend!!!! :guitar:

---

### Post by crazyfuturamanoob on 2008-11-08
Try running it from console, then you might get an error message.

---

### Post by Georgia boy on 2008-11-08
What do you mean by running from console? I went to the applications, clicked on games then clicked on the OpenArena. Like I said, I got a blank screen flash at me then it went back to my desk top. Lost me when you say to try from console. Do you think that the game didn't load or maybe something else?


I like the games that I've seen so far. Have trouble with some of them like the sim stuff but otherwise not too bad on others.

Thanks
Tom

---

### Post by Perfect Storm on 2008-11-08
console (KDE) = terminal (Gnome)

You'll find it in Applications tab ---> Accessories ---> Terminal

You can see which command to launch OpenArena by editing the Open Arena Launcher.

---

### Post by crazyfuturamanoob on 2008-11-08
Applications --> Accessories --> Terminal

Type in "openarena" and press enter.

Now there will appear text on the window.
Post all the output here, so we can say what's wrong.

---

### Post by Georgia boy on 2008-11-08
Will do. Downloading the game again now. Will try and see what happens. If same problem, will post what I get from the terminal. Sorry about the confusion of terms between the console and terminal.

Thanks
Tom

Here is what I got from the terminal:

ioQ3 1.33+oa linux-i386 Oct 28 2007
----- FS_Startup -----
Current search path:
/home/thomas/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (76 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3573 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
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


I don't have a joystick. I don't need to play this in Wine do I? Don't have that installed. Any simple solutions?

Thanks
Tom

---

### Post by eragon100 on 2008-11-08
What video card do you have? Have you got the 3d drivers installed?

---

### Post by Georgia boy on 2008-11-08
Have a NVIDIA GeForce 7300LE Graphics Card. Don't know about the rest. 
Tom

---

### Post by noerrorsfound on 2008-11-09
System > Administration > Hardware Drivers

You need a proprietary driver installed to play 3d accelerated games.

---

### Post by alwayshere on 2008-11-09
copy past below 4 line and past into terminal and oush enter  

sudo apt-get install cl-sdl
sudo apt-get install cl-sdl-img
sudo apt-get install cl-sdl-mix
sudo apt-get install cl-sdl-opengl

then below line and push entre 

sudo apt-get update

now try the game

---

### Post by Georgia boy on 2008-11-11
Did the System Admin. Hardriver. Enabled the Nvidia. Now was able to view the Open Arena. Thanks!!! 

What are those lines that you want me to paste into the terminal? What will they do?

Also, where can I find the instructions for playing? Seems like I'm shooting at everyone due to not knowing who is who. Looks to be an interesting game though. Did notice that I now have na Icon at the top of the screen telling me that New restricted drivers in use. If NVIDIA came with the computer why is this listed as restricted? Means I have to go to Windows once in a while to check for updates and see that it stays good?

Thanks everyone for all help!!! Really appreciated.

Tom

---

### Post by crazyfuturamanoob on 2008-11-11
These lines will install lisp bindings for SDL.

```
sudo apt-get install cl-sdl
sudo apt-get install cl-sdl-img
sudo apt-get install cl-sdl-mix
sudo apt-get install cl-sdl-opengl
```

And this one will download updates, obviously.

```
sudo apt-get update
```

alwayshere probably wanted you to run these lines in case OpenArena needs
those SDL libraries to run.

---

### Post by noerrorsfound on 2008-11-11
> **Georgia boy said:**
> Did notice that I now have na Icon at the top of the screen telling me that New restricted drivers in use. If NVIDIA came with the computer why is this listed as restricted? Means I have to go to Windows once in a while to check for updates and see that it stays good?
No, it's simply informing you that the restricted drivers you chose to install were installed successfully. "Restricted" is used to mean that they are closed source. Since they're closed source, only NVIDIA can improve them and fix bugs, unlike open source software that could be modified by anyone.

---

### Post by alwayshere on 2008-11-12
glad to hear you got it going im not to sure how openarena is going these days but if you want another game to try sauerbraten is a good fps  go to add/remove and searh sauerbraten and you should find it 

or in terminal put 

sudo apt-get install sauerbraten

---

### Post by Georgia boy on 2008-11-13
Thanks for the help. Hey alwayshere, went to the add/remove. Didn't find the game you mentioned. Guess when I get time, I'll go to the terminal and try getting it that way. Any more ideas of some fun FSP games? OpenArena looks good, once I find the instructions as to what is going on. 

Thanks everyone!!
Tom

:guitar:

---

### Post by Irritant on 2008-11-13
> **Georgia boy said:**
> Any more ideas of some fun FSP games?:guitar:

[http://red.planetarena.org](http://red.planetarena.org)

---

### Post by detrate on 2008-11-16
> **Georgia boy said:**
> Any more ideas of some fun FSP games?

[http://www.nexuiz.com](http://www.nexuiz.com)

---

### Post by crazyfuturamanoob on 2008-11-16
> **Georgia boy said:**
> Any more ideas of some fun FSP games?

Urban Terror is like Counter-Strike but a lot better & more realistic. Graphics are very good.

Give it a shot. Here's a tutorial how to install: [[COLOR="Blue"]http://gaming.gwos.org/doku.php/guides:64bit:urban_terror[/COLOR]](http://gaming.gwos.org/doku.php/guides:64bit:urban_terror)

[img]http://www.urbanterror.net/e107_plugins/randompic_menu/images/shot0015.jpg[/img]

---

### Post by Georgia boy on 2008-12-07
Hi. Go the Open Arena going. Getting my butt kicked while learning but having fun. Thanks guys.
Tom

---

