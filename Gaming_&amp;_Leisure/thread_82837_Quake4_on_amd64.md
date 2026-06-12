---
title: "Quake4 on amd64?"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by rseymour on 2005-10-27
I think I've followed the install instructions.  when I try to run ./quake4, it looks like it's trying to load, in fact I do get the sound.  I don't get any video ... just a blacked out screen that requires a power off to get out of?

I initially had the libSDL issue.  I "copied" the libSDL file from my nwn install into a lib directory under quake4, created a link for libSDL-1.2.so.0, and added to the path in the quake4 script. (I'd read on forum that you need a 32-bit lib)

I have nvidia's 6800 chipset, get the splashscreen on boot, can run glxgears, doom3, and nwn, so I think the drivers are configured.

I "installed" into a directory under my home and changed the file/folder permissions.

any thoughts about getting the video running?

---

### Post by threexone on 2005-10-27
Could you just please tell me how exactly how you "created a link for libSDL-1.2.so.0, and added to the path in the quake4 script"

Because I can't even start the game. I have the libSDL file taken from UT2004 and copied it into the quake folder. But then i'm stuck.

---

### Post by seethru on 2005-10-27
does it give you any errors at all regarding video?

---

### Post by rseymour on 2005-10-27
[COLOR="Red"]does it give you any errors at all regarding video?[/COLOR]

no errors at all ... after entering ./quake4, full screen goes blank, I get a momentary mouse cursor, and then screen blanks again ...

[COLOR="Red"]Could you just please tell me how exactly how you "created a link for libSDL-1.2.so.0, and added to the path in the quake4 script[/COLOR]"

from nwn, file is libSDL-1.2.so.0.0.5.  I created a lib directory under quake4 and then copied the file into the newly created directory.  from w/i the directory  "ln -s libSDL-1.2.so.0.0.5 libSDL-1.2.so.0"  make sure your permissions are still ok.

my quake4 file looks like:

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/rseymour/quake4"
export LD_LIBRARY_PATH=./lib:$LD_LIBRARY_PATH:.
./quake4.x86 $*
exit $?

---

### Post by crane on 2005-10-27
Not real sure about this but I believe there were some issues with quake4 not running on 64 bit OS. I also found this at[http://zerowing.idsoftware.com/linux/quake4/]("http://zerowing.idsoftware.com/linux/quake4/")

> Crashes on startup when loading the game module

Some Debian and Debian-based distributions ( like Ubuntu ) are crashing during startup. It appears this is caused by the SDL packages selection. You need to install libsdl1.2debian-alsa or libsdl1.2debian-oss instead of libsdl1.2debian-all.

FYI, it is not clear what happens with this crash. Happens during initialization of static variables, has to do with a cvar named g_log and goes away if renamed to something else. So it would look like this version of SDL has g_log already defined from somewhere else and the dynamic loader getting confused over it. 

---

### Post by threexone on 2005-10-28
Thank you, I'll have a go tonight after work.

---

### Post by rseymour on 2005-10-28
> Quote:
Crashes on startup when loading the game module

Some Debian and Debian-based distributions ( like Ubuntu ) are crashing during startup. It appears this is caused by the SDL packages selection. You need to install libsdl1.2debian-alsa or libsdl1.2debian-oss instead of libsdl1.2debian-all.

FYI, it is not clear what happens with this crash. Happens during initialization of static variables, has to do with a cvar named g_log and goes away if renamed to something else. So it would look like this version of SDL has g_log already defined from somewhere else and the dynamic loader getting confused over it.

I'd seen this and also seen from a poster where the "alsa" was working (thanks for the suggestion, tho) ... I was originally configured with oss (seemed to work with nwn & doom3), but it didn't work with quake4.  tried installing the "alsa" version  (nwn and doom3 still seem to work?), but it hasn't helped with quake4.

just tried reinstalling as "default" (/usr/local/games/quake4) ... no change ... still get the sound, but no video :( 

think i'll call it a night.

---

### Post by rseymour on 2005-10-28
Well, It looks like I'm almost there?

It finally dawned on me that the cursor I see before the screen blanks the last time is very "large".  I know that doom3 runs at 800x600 w/o using the 500MB for texture memory at 1024x768, so I tried resetting my screen resolution (normally I have it set at 1280x1024) to 800x600.

And I have video!  The first time I exited, I reset my desktop to 1280x1024 and tried again ... I still had video.  However since then, I've shut down and can only get video if I first set my desktop to 800x600.

I'll keep after it, but at least I can try out the game now.

(btw, in the process of trying to figure out what was going on, I did try libSDL ... all.  Didn't kill the sound.  Also seemed not to effect nwn and doom3.  However, I since have gone back to the oss version.)

---

### Post by blueblood on 2005-10-31
Hey.
I installed Ubuntu yesterday and got the most basic stuff working, videocard and sound.
But when I tried Q4 I got the libSDL error

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory


I see some of you have solved this, could you please explain?
And I saw that some used another libSDL 32bit file? Were do I get it? Is it possible someone could put it up on and FTP site for me to download?
Would really appriciate all help I could get, Quake is my life :)

Best regards
Jesper (aka blueblood)

---

### Post by rseymour on 2005-10-31
> And I saw that some used another libSDL 32bit file? Were do I get it? Is it possible someone could put it up on and FTP site for me to download?

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html) ... at the very bottom of the pg are download links

---

### Post by blueblood on 2005-10-31
[QUOTE=rseymour][http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html) ... at the very bottom of the pg are download links[/QUOTE]

Thanks!

But, do I install it first?
Then copy the file from../lib/something?

---

### Post by rseymour on 2005-10-31
check the link above ... #4, the second part

---

### Post by thread on 2005-11-01
I get the same error about the missing libSDL.

```
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```

Who can put into step-by-step terms what one has to do to get quake4 to run on AMD64? Someone said they needed to install (via a chroot) a 32bit libsdl for quake4 because it won't work wtih the 64bit libsdl... but how exactly is that done?

I've encountered one other program that has a very similar message:

```
./mixxx: error while loading shared libraries: libmad.so.0: cannot open shared object file: No such file or directory
```

Is there a standard procedure for getting 32bit versions of the libs I need on my system?

---

### Post by EmilianoFraga on 2005-11-01
Hi guys,

I've got Q4 running on my Ubuntu-AMD64 box. :p

That's what I've done:

I followed the instructions on [http://skuld.bmsc.washington.edu/~yi/blog/?p=6]("http://skuld.bmsc.washington.edu/%7Eyi/blog/?p=6")

After this, quake4 ran for the first time, but nothing was presented on the screen.

I thought that it could be a problem with nVidia drivers and libraries. So I installed [FONT=Courier New]nvidia-glx-ia32[/FONT] and tried again.

This time quake 4 reported an error when loading video libraries. I abort this approach and removed nvidia-glx-ia32.

Reading other messages in this thread, I figured that the screen problem is related with my desktop resolution. After lowering res. (use CTRL ALT -), Quake 4 finally appears on my monitor.

Very good, but not enough, 'cause the game sound was very odd, a bit noisy.

I figured that the above solution has alsa drivers, wich doesn't work fine in my Ubuntu.

So, I've switched to oss:

[libsdl1.2debian-oss_1.2.7+1.2.8cvs20041007-3ubuntu4_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian-oss_1.2.7+1.2.8cvs20041007-3ubuntu4_i386.deb")

...and installed it:

```
 dpkg -X libsdl1.2debian-oss_1.2.7+1.2.8cvs20041007-3ubuntu4_i386.deb /emul/ia32-linux/
``` 
So, with the right 32 bit SDL libraries and video resolution, I've started quake 4 (with oss):

```
 ./quake4 +set s_driver oss
``` 
Great! Quake 4 is now running flawlessly. :KS

I hope that could be useful and clear enough.

Regards,

Emiliano

---

### Post by blueblood on 2005-11-03
Hey,

I followed this guide: [http://skuld.bmsc.washington.edu/%7Eyi/blog/?p=6](http://skuld.bmsc.washington.edu/%7Eyi/blog/?p=6)

And now I get an error saying:

Sys_Error: SDL_GL_LoadLibrary libGL.so.1 failed: Could not load OpenGL library

Whats up with that?
I got the libGl.so.1 in /usr/lib, and that path is also in ld.so.conf, and I did run ldconfig.

---

### Post by siman on 2006-03-10
on my 64bit machine, I also had to copy the 32bit sdl files into quake directory to get it to start.

Now I only have sound, I tried lowering my screen resolution from 1280 to 1024 and 800.. before the game and during with the keykombo... only black screen, not even mouse pointer.

any ideas what I should try?

---

### Post by siman on 2006-03-11
in reply to myself:

I found this in the d3 FAQs

[http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage?action=show&redirect=FrontPage#head-37a70860392f09490de7dde78bea00dba55c707a](http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage?action=show&redirect=FrontPage#head-37a70860392f09490de7dde78bea00dba55c707a)

But I don't know what this glxinfo thing should tell me or how I can change the bpp in Ubuntu.

My xorg.conf has a line that says 

```
	DefaultDepth	24 
```

.. so I'm running 24 bit?

---

### Post by Ubuntuud on 2006-03-11
I think that's your colordepth, if you were running 24 bit, you could only have less than 20 MB RAM (2^24).

---

### Post by lotheac on 2006-03-15
Hey. If any of you still get that libSDL not found error message and are using Dapper, try installing the [FONT="Courier New"]ia32-libs-sdl[/FONT] package.

---

### Post by mesp on 2006-05-04
[QUOTE=EmilianoFraga]Hi guys,

I followed the instructions on [http://skuld.bmsc.washington.edu/~yi/blog/?p=6]("http://skuld.bmsc.washington.edu/%7Eyi/blog/?p=6")


Emiliano[/QUOTE]


Damn the link no longer exists
have same problem on kubuntu amd64 breezy 5.1
any one able to help

---

### Post by R3linquish3r on 2006-05-07
Do what I did....

Install the 32x version of Ubuntu :P

Little less performance but life is so much happier :)

One day the x64 version will be better supported.... One day....

---

### Post by gonesolo on 2006-05-20
[QUOTE=lotheac]Hey. If any of you still get that libSDL not found error message and are using Dapper, try installing the [FONT="Courier New"]ia32-libs-sdl[/FONT] package.[/QUOTE]


This worked perfectly for me thanks

Now I just got to work out the sound issue

Dapper Drake Flight 6 (64 bit)
AMD 3800
2GB RAM
Nvidia 6800

---

### Post by crane on 2006-05-21
Just as a note. If you have this problem and you already have UT2004, Doom3, or AA installed just get the file out of hose games.
 I simply copied the file from UT2994 into the Quake4 folder and all is good!
 You will have to do a search to find it. I believe it is in the system folder in UT2004.

---

### Post by mogelhead on 2006-06-21
[QUOTE=lotheac]
Hey. If any of you still get that libSDL not found error message and are using Dapper, try installing the ia32-libs-sdl package.[/QUOTE]

[QUOTE=gonesolo]This worked perfectly for me thanks

Now I just got to work out the sound issue

Dapper Drake Flight 6 (64 bit)
AMD 3800
2GB RAM
Nvidia 6800[/QUOTE]
I agree with gonesolo.

I have installed Kubuntu 6.06 (Dapper) 64 bit and when I tried to launch the Quake 4 demo, I got the error "./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory".

But after installing ia32-libs-sdl it disappeared and I could play the game.

From the package description:
"This package contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Ubuntu system running a 64-bit kernel. These are packages related to sdl. Commercial games like Quake4 are known to work with this package installed."

---

