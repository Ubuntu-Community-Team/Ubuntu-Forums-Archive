---
title: "Tremulous Problem"
date: 2006-06-16
forum: Gaming &amp; Leisure
---

### Post by JPMaximilian on 2006-06-16
I ran the Tremulous install script, however, when I try to run the game I get the following output:

 tremulous
tremulous 1.1.0 linux-x86 Feb 28 2006
----- FS_Startup -----
Current search path:
/home/jtelt/.tremulous/base
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
Received signal 11, exiting...
----- CL_Shutdown -----
RE_Shutdown( 1 )
*** glibc detected *** corrupted double-linked list: 0xb7e9d358 ***
DOUBLE SIGNAL FAULT: Received signal 6, exiting...

Any help would be appreciated.

---

### Post by Perfect Storm on 2006-06-17
Looks like you havn't set up 3D acceleration for your graphic card.

---

### Post by eqisow on 2006-06-17
[https://wiki.ubuntu.com/BinaryDriverHowto]("https://wiki.ubuntu.com/BinaryDriverHowto")

---

### Post by JPMaximilian on 2006-06-18
Thanks for the replies, I tried following the directions in the above link, but when I run: 

sudo nvidia-glx-config enable

I get the following error:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

I run md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum and it breaks my X server, so I can't get to a desktop.  I had to restore my old version in order to get back into X.  Any ideas?

---

### Post by puppetj on 2006-07-12
Sorry to ask about this but i'am new to linux in some ways, how do i even install this i ran in the term as root the ./ command but i get permission denied, whats a .run ext anyway? btw is there another easy way to install rpm's without all the "alien" confusing things ie. all the files i need like pearl,rpm man,and all that other crap can't i just get a simple install that installs rpms for debain/ubuntu ](*,)

---

### Post by scxtt on 2006-07-12
did you make the tremulous-1.1.0-installer.x86.run file executable?
[indent]chmod 755 tremulous-1.1.0-installer.x86.run
./tremulous-1.1.0-installer.x86.run[/indent]

---

### Post by puppetj on 2006-07-12
ok thanks fast replay, but after install i got a opengl error well this is running in vmware workstation 5.5.1 with the vmware tools installed how can i get this ruuning? and btw chmod or all run? what does it do?

---

### Post by rapha on 2006-08-23
Uh, why the heck would you want to run Tremulous in VMWare? They got a perfectly fine native package. (Even if you still wanted to, you couldn't: VMWare doesn't offer 3D acceleration). After you've successfully followed the BinaryDriver howto (check with glxinfo), installing tremulous should be a simple matter of "sh tremulous-1.1.0-installer.x86.run" (no need to use chmod really).

---

