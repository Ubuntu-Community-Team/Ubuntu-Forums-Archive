---
title: "Wine Gaming Help Needed"
date: 2006-06-10
forum: Gaming &amp; Leisure
---

### Post by Eman64 on 2006-06-10
Ok here's the deal. I Installed a few games such as Majesty Gold, Quake 3 and Diablo 2 but when I try to load any of them I always get a message saying couldn't find quake3.mpq So yeah, Im stuck ](*,)

---

### Post by echo $USER on 2006-06-10
Are you launching the program in the executable's directory?

---

### Post by Eman64 on 2006-06-10
I've tried but I can't find the directory because when I tried to install the games it wouldn't let me create a directory in Z: so I had to make them under C:Program Files\Diablo 2

---

### Post by echo $USER on 2006-06-10
It will be here:> ~/.wine/Program\ Files/Diablo 2All the files in your home directory that are hidden begin with a > .You can display them wiht this command> ls -a

---

### Post by Eman64 on 2006-06-10
Ok now im getting 

Q3 1.11 win-x86 Nov 24 1999
----- FS_Startup -----
Current search path:
Z:\home\******/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
Z:\home\******/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
Couldn't load default.cfg

for Quake but D2 is working so thanks for that

---

### Post by Dullin on 2006-06-11
Quake 3 can be installed nativly on linux without the help of wine. That might be an easier solution to your current problem.

---

### Post by Eman64 on 2006-06-11
[QUOTE=Dullin]Quake 3 can be installed nativly on linux without the help of wine. That might be an easier solution to your current problem.[/QUOTE]

Really? Would you mind finding a link on how to do this?

---

### Post by eqisow on 2006-06-11
Quake 3 in Linux:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3")
[http://www.neowin.net/forum/lofiversion/index.php/t252074.html]("http://www.neowin.net/forum/lofiversion/index.php/t252074.html")

---

### Post by Eman64 on 2006-06-11
Cool. Thanks Everybody

---

### Post by Eman64 on 2006-06-12
Crap. I installed Quake the way the websites told me to and and when i use the quake3 command it just doesn't work. It blackens the screen, then it just pops my desktop back. ](*,)](*,)

Update: I ran the quake3 command in the terminal and got this

```
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/username/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
--------------------------------

```

Update 2.0:
OK I copied the q3config.cfg file into the quake3 folder but i've searched my whole system and the cd and cant find the autoexec.cfg file

---

### Post by Eman64 on 2006-06-13
Ok I think I found out why it's not working. I need a new Video Card. Do any of you guys recommend a certain brand? I'm aiminng for a 128MB.

---

### Post by eqisow on 2006-06-13
From what you've said, I wouldn't really diagnose your video card as the problem. If you've discovered something else that lef you to this belief, please share. :)

That being said, if you get a new card you definitely want an nVidia, and my favorite manufacturer is BFG Tech. They're a bit more expensive, but they offer lifetime warrantees and excellent support. Their stuff also comes overclocked out of the box.

Also, the ammount of memory isn't really the biggest factor when it comes to performance. For example, a newer 128 MB card will usually trounce an older 256 MB card in almost every test. (Extreme high resolutions being the possible exception)

I could make more specific recomendations if you want to throw out a dollar figure and your other system specs.

---

### Post by Eman64 on 2006-06-13
> From what you've said, I wouldn't really diagnose your video card as the problem. If you've discovered something else that lef you to this belief, please share.
Really? Well my brother thought that was the problem but if you have other suggestions to my problem please post them before I spend any money on a new card.

---

### Post by eqisow on 2006-06-13
I'm afraid I don't have a suggestion. It's easier to know what the problem's not than to know what it is. :(

---

### Post by Eman64 on 2006-06-15
TREMULOUS
```

user@computer:~$ tremulous
tremulous 1.1.0 linux-x86 Feb 28 2006
----- FS_Startup -----
Current search path:
/home/user/.tremulous/base
/usr/local/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/local/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/local/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/local/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/local/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/local/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/local/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/local/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/local/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/local/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/local/games/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
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
Using 8/8/8 Color bits, 16 depth, 8 stencil display.
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
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


```

QUAKE 3
```

user@computer:~$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/user/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
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
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


```

Right so thats what I get when I try to run Tremulous and Quake 3. Maybe They aren't running the right thing for my Video Card maybe?

---

### Post by Jasper Houtman on 2006-06-15
Prob wont execute because you installed the games as root and don't have the permissions to execute the files as a normal user.

Try to start up the game using sudo "program" and see if that works.

*edit* 

Also noticed that your hardware acceleration is disabled!! 
Neither game will run without it! 
Check if you have the correct and latest driver for your videocard.

---

### Post by Eman64 on 2006-06-15
[QUOTE=Jasper Houtman]
Also noticed that your hardware acceleration is disabled!! 
Neither game will run without it! 
Check if you have the correct and latest driver for your videocard.[/QUOTE]

Umm yeah, I'm ok at Linux but am still learning. I would check that how?

---

### Post by tronica on 2006-06-16
what video card to you have?

for nvidia try here on how to install it:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

for ati cards

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by polpak on 2006-06-16
Or you can just use the Binary Driver HOWTO from the wiki..

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

BTW, to see if you have hardware accelleration, a simple

glxinfo  | grep direct

Should report back that direct rendering: Yes. Otherwise you don't have hardware accelleration.

---

### Post by Eman64 on 2006-06-18
```
quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/user/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


```

Yeah So thats what I get when I try to run Quake after setting up my vid card.

---

### Post by crane on 2006-06-18
What video card are you running? Nvidia? if so are you geting the nvidia screen when X starts? Have you restarted you Xserver? (ctrl-alt-backspace)
Quake 3 should be fairly painless to get working. Did you install as a user or by sudu?
Either way you should be able to type quake3 in a terminal and launch it.
The autoexec.cfg Iis a file you create. it just contains cusom settings you want to use.
When running as a user (which is th ebest way) you working directory is actually a hidden file in you home folder.
 Open you file browser to home directory and show hidden files (ctrl-h in gnome) you will now see a file called .quake3
The autoexec.cfg as well as any other configs should go in the baseq3 directory in that folder,

---

### Post by Eman64 on 2006-06-18
I'm running a  nvidia NV11 [GeForce2 MX/MX 400]

Ok so now after doing all of that, when I run Quake 3 it blacks out and then my screen comes up magnified. This seriously is no fun because until this works i have to use my brothers slow windows pc to frag

---

### Post by Eman64 on 2006-06-21
Ok, I really don;t know where to look to see what type of Video Card I have but when I went into device manager I saw Virtual PCI-to-PCI bridge (AGP) and NV11 [GeForce2 MX/MX 400] in its field. If that's not it I screwed up.

---

### Post by Eman64 on 2006-06-27
[QUOTE=crane]What video card are you running? Nvidia? if so are you geting the nvidia screen when X starts? Have you restarted you Xserver? (ctrl-alt-backspace)
[/QUOTE]

No I don't think I am getting the screen when i start up. But i checked and my mavhine definetly has my nvidia as its default card

---

### Post by crane on 2006-06-28
If it does have an nvidia card, you first need to install the nvidia-glx driver for your system. This will enable you to run 3d applications.
 Search the forums and check the how tos. Installing the driver is pretty painless.
 Once this is done you should be able to run Q3!

---

### Post by jonifen on 2006-06-29
I followed the instructions as per [http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") and it works fine for me.

Hope that helps, and you get your game working soon :)

---

### Post by Eman64 on 2006-07-09
Ok, I got it to work. In case you guys want a match, My name is 3M4N and my bro is RocktheCasbah.

We play tremulous and quake 3

---

### Post by asterisc on 2006-07-10
hi there,

i have the same problems (playin games with wine).
So far, i tried to run: Insane (an old car game), and CounterStrike.
For both games, it start the menu, then stay there. 
Should i install some things? (directX on they virtual drive, or something?) 

regards

---

