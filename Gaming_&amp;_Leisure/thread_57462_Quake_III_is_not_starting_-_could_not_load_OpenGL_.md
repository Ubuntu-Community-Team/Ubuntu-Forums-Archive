---
title: "Quake III is not starting - could not load OpenGL subsystem"
date: 2005-08-16
forum: Gaming &amp; Leisure
---

### Post by AndreasMeier on 2005-08-16
Hi,

I installed Quake III today on my Kubuntu 5.04.
I have a ATI 9600 with the ATI drivers installed, OpenGL is working fine, so I thought, Quake III should be no problem, but when I start Quake III, I get the following error :
./baseq3/pak0.pk3 (3539 files)
./baseq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: mars
IP: 127.0.0.1
----- R_Init -----
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf or curre                                                                                                  nt dir: /usr/local/games/quake3/libGL.so: cannot open shared object file: No suc                                                                                                  h file or directory
failed
...loading libMesaVoodooGL.so: QGL_Init: Can't load libMesaVoodooGL.so from /etc                                                                                                  /ld.so.conf or current dir: /usr/local/games/quake3/libMesaVoodooGL.so: cannot o                                                                                                  pen shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem



In this [thread](http://ubuntuforums.org/showthread.php?t=52693&highlight=quake+opengl) 
I read that Quake is expecting a libGL.so, but Ubuntu is only having a libGL.so.1.

My question is, if I have exactly this problem, too ??
And I do not understand, what is meant by "codered +set r_gldriver libGL.so.1" in the other posting,
or how I can get rid of this problem.

Thank in advance,
regards,
Andreas

---

### Post by hammett111 on 2005-08-16
[QUOTE=AndreasMeier]Hi,

I installed Quake III today on my Kubuntu 5.04.
I have a ATI 9600 with the ATI drivers installed, OpenGL is working fine, so I thought, Quake III should be no problem, but when I start Quake III, I get the following error :
./baseq3/pak0.pk3 (3539 files)
./baseq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: mars
IP: 127.0.0.1
----- R_Init -----
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf or curre                                                                                                  nt dir: /usr/local/games/quake3/libGL.so: cannot open shared object file: No suc                                                                                                  h file or directory
failed
...loading libMesaVoodooGL.so: QGL_Init: Can't load libMesaVoodooGL.so from /etc                                                                                                  /ld.so.conf or current dir: /usr/local/games/quake3/libMesaVoodooGL.so: cannot o                                                                                                  pen shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem



In this [thread](http://ubuntuforums.org/showthread.php?t=52693&highlight=quake+opengl) 
I read that Quake is expecting a libGL.so, but Ubuntu is only having a libGL.so.1.

My question is, if I have exactly this problem, too ??
And I do not understand, what is meant by "codered +set r_gldriver libGL.so.1" in the other posting,
or how I can get rid of this problem.

Thank in advance,
regards,
Andreas[/QUOTE]

Okay, people corfect me if I'm wrong. When you run quake3 from the command line type your command ./quake3 and then add after it "codered +set r_gldriver libGL.so.1" so it looks like ./quake3 codered +set r_gldriver libGL.so.1. This will run the game with libGL.so.1.

You could also link libGL.so.1 as libGL.so, so that Quake3 recognizes it as the .so.

I hope this isnt too vague.

---

### Post by crane on 2005-08-16
[QUOTE=hammett111]Okay, people corfect me if I'm wrong. When you run quake3 from the command line type your command ./quake3 and then add after it "codered +set r_gldriver libGL.so.1" so it looks like ./quake3 codered +set r_gldriver libGL.so.1. This will run the game with libGL.so.1.

You could also link libGL.so.1 as libGL.so, so that Quake3 recognizes it as the .so.

I hope this isnt too vague.[/QUOTE]

That would work if you were executing from thr quake3 directory. Quake3 install a script in /bin so you shouldn't have to use ./quake3. Just type quake3 codered +set r_gldriver libGL.so.1.
I do not use ati video card though. What is the codered doing?

---

### Post by AndreasMeier on 2005-08-17
Ok, I will try that in the evening.
Yesterday I had a look in the /usr/X11/lib.
There were two files: libGL.so.1 and libGL.so.1.2, first was only a symbolic link to the second one.
So I thought, why not creating a symlink for libGL.so to libGL.so.1.2, but it didnt work.

Should I adapt your line as follows:
./quake3 codered +set r_gldriver libGL.so.1.2

??

Regards
Andreas

---

### Post by AndreasMeier on 2005-08-17
Ok, now Quake is running fine, thanks for that.

But I figured out, that I have another problem with OpenGL.
I have dualscreen configured, but when I start for example Chronium, the window is displayed, but the content IN the window is shifted to the left.
That also happened to Quake.
Please see the screenshot.

I dont know what this mean, normal office apps are displayed correctly.

In hope for any help
Regards
Andreas

PS: Da**, why is an upload of 1 jpg not working here ? After pressing "upload", I get a blank screen in the popup window

---

### Post by AndreasMeier on 2005-08-17
And here is the screenshot, that I posted on "linuxforen.de" - there the attachement function is working  :???: 
[Link to screenshot](http://www.linuxforen.de/forums/attachment.php?attachmentid=13625) 

Regards
Andreas

---

