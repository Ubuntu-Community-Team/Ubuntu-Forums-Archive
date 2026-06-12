---
title: "[SOLVED] Installing phun"
date: 2008-02-24
forum: Gaming &amp; Leisure
---

### Post by Sordelka on 2008-02-24
I need a detailed explanation of how to install this game. I got the archive, and now am looking at a bunch of files; I have no idea what they do.

---

### Post by abadtooth on 2008-02-24
Just in case anyone else has this problem. 


Phun does not install, all you need to do is make sure the file called "Phun" is allowed to execute via "Right click/Properties/permissions" and make sure "allow executing file as a program"
Then simply right click it and click open/Run.
[URL="http://abadtooths.com/2008/02/19/forget-crayon-physic-hello-phun/"]
http://abadtooths.com/2008/02/19/forget-crayon-physic-hello-phun/[/URL]

---

### Post by Sockerdrickan on 2008-02-24
Why does people always want to install something when it's small and runnable from the current dir without problem?

---

### Post by Sordelka on 2008-02-24
To answer your question: simply because on their site they write that it is a source code archive.... Source code needs to be compiled....

---

### Post by Sockerdrickan on 2008-02-24
It's not open source.

---

### Post by Sordelka on 2008-02-24
Ok Ok but I am used too much to the compiling/configuring procedure that when it comes to easy stuff, I get lost!

---

### Post by klas_katt on 2008-02-27
This is NOT solved, klicking the executable (64bit) does NOTHING. 
(I use konqueror.)

---

### Post by Sockerdrickan on 2008-02-27
Run it from a terminal and paste the output here!

---

### Post by klas_katt on 2008-02-27
```
~/.phun/Phun$ phun
phun: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory
```

libGLEW.so.1.5 is there in the same folder, I have version 1.4 installed as well.
I don't know if i have SDL_image or the libraries mentioned in the README.txt
Can't find SDL_image on the SDL homepage, is it included in SDL?

---

### Post by Toadmund on 2008-02-27
I use firefox (64 bit) also does nothing.

---

### Post by Sockerdrickan on 2008-02-27
> **klas_katt said:**
> ```
~/.phun/Phun$ phun
phun: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory
```

libGLEW.so.1.5 is there in the same folder, I have version 1.4 installed as well.
I don't know if i have SDL_image or the libraries mentioned in the README.txt
Can't find SDL_image on the SDL homepage, is it included in SDL?

```
LD_LIBRARY_PATH=. ./phun
```:guitar:

---

### Post by klas_katt on 2008-02-28
[SOLVED] again. It just works, thanks. The problem was I didn't know how to use the library. Phun is awesome.

---

### Post by forrestcupp on 2008-02-28
> **klas_katt said:**
> ```
~/.phun/Phun$ phun
phun: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory
```

libGLEW.so.1.5 is there in the same folder, I have version 1.4 installed as well.
I don't know if i have SDL_image or the libraries mentioned in the README.txt
Can't find SDL_image on the SDL homepage, is it included in SDL?

Supposedly this was fixed in the newest version.  The problem is that it didn't know the correct current working directory.  This problem could happen in a number of programs you try to run.  If it weren't fixed, the way to get it to work is to either add it to your paths like Tux0r said, or to change to that directory before you run the executable.

Don't type:
```
/home/username/Phun/phun
```
But instead type:
```
cd ~/Phun
./phun
```
That way your Phun directory is the current working directory.  I've had the same problem running some programs with wine, too.

---

### Post by sbubba on 2008-02-28
hello, I've another problem with phun:
```
speppa@sbubbo:~/Phun$ LD_LIBRARY_PATH=. ./phun
workdir = /home/speppa/Phun/
Parsing /home/speppa/Phun/autoexec.cfg...
Creating window...
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: X11 driver not configured with OpenGL
Exception caught: Couldn't set video mode, SDL-error: X11 driver not configured with OpenGL
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: X11 driver not configured with OpenGL

```

I've tried with  LD_LIBRARY_PATH=. ./phun but nothing happened :confused:

---

### Post by forrestcupp on 2008-02-29
You have to have a video card and drivers with 3D support even though the game is not 3D.  It uses OpenGL.

---

### Post by sbubba on 2008-03-01
> **forrestcupp said:**
> You have to have a video card and drivers with 3D support even though the game is not 3D.  It uses OpenGL.
oh yes, I've also cheked with
```
speppa@sbubbo:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

---

### Post by Toadmund on 2008-03-04
Why is the 64 bit linux version of Phun an .exe?

I can't get this to run :(

Wine doesn't even work, doesn't even open (hardy)

Any 64 bit users having any Phun?

---

### Post by bobpaul on 2008-03-05
> **Toadmund said:**
> Why is the 64 bit linux version of Phun an .exe?


Sure you didn't download the 64bit windows version? I *just* downloaded the 64bit linux version and the binary is just called "phun". No extension.

---

### Post by Toadmund on 2008-03-05
Does your Phun folder look like this? (attachment)

If so How did you get it to run?
And look, the 64 bit version is a zip file, while the 32 bit version is a tar?
[http://www.acc.umu.se/~emilk/downloads.html]("http://www.acc.umu.se/~emilk/downloads.html")

Is there another download site I should be aware of?

---

### Post by Toadmund on 2008-03-05
Sorry here is the attachment.

---

### Post by Bandarra on 2008-03-07
I also tried installing the game but no banana...
even after installing every package I could find with SDL on it it still doesn't run and  displays the following errors:
```
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
```

Any ideas please?

---

### Post by fishyf on 2008-03-08
I get the same error.

The output of
 lspci | grep -i graphics
is
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

And I'm running compiz.

---

### Post by Bandarra on 2008-03-09
I really wanted to get this "game" going... :confused:

any ideas?

---

### Post by bobpaul on 2008-03-09
> **Toadmund said:**
> Does your Phun folder look like this? (attachment)
 
Yes. That's what mine looks like.
> If so How did you get it to run?

First I installed the correct graphics drivers so that Direct Rendering (DRI) was working.  Check with 'glxinfo | grep direct'. Then I installed the libsdl1.2-all package. Then I made the "phun" file executable. Finally, I ran the program as Tuxor suggested.

```

~$ glxinfo | grep direct
direct rendering: Yes             #<-- Graphics drivers installed correctly
~$ sudo aptitude install libsdl1.2-all
 ...
~$ cd Phun
~/Phun$ chmox +x phun
~/Phun$ LD_LIBRARY_PATH=. ./phun

```
> And look, the 64 bit version is a zip file, while the 32 bit version is a tar?
[http://www.acc.umu.se/~emilk/downloads.html]("http://www.acc.umu.se/~emilk/downloads.html")
That is correct. The 64bit version for linux is a *.zip file. however, it contains no *.exe files.
> Is there another download site I should be aware of?
Not that I know of. That's the one I used.

---

### Post by eks on 2008-03-10
Also on 64 without any phun, I mean, luck.

But I get:

```

~/Desktop/Phun$ ./phun 
./phun: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory

```

While both libGLEW and libGLEW-dev are installed.

ARGH, just noticed, libglew on repos are 1.4, while it requests 1.5. Why? :(


eks
PS: downloaded [this]("http://www.acc.umu.se/~emilk/files/Phun_beta_3_12_linux64.zip") at [http://phun.cs.umu.se/wiki/Download](http://phun.cs.umu.se/wiki/Download)

---

### Post by bobpaul on 2008-03-10
> **eks said:**
> Also on 64 without any phun, I mean, luck.
ARGH, just noticed, libglew on repos are 1.4, while it requests 1.5. Why? :(


libglew1.5 is in the phun folder. You need to set the LD_LIBRARY_PATH variable to tell phun to search for libraries in the current folder. This has been noted multiple times, most recently in my last post.

Instead of
```

~/Desktop/phun$ ./phun 

```

use
```

~/Desktop/phun$ LD_LIBRARY_PATH=. ./phun

```

This sets the path variable to "." for the current command (./phun). Note the space between the two '.'s

---

### Post by Bandarra on 2008-03-12
> **Bandarra said:**
> I also tried installing the game but no banana...
even after installing every package I could find with SDL on it it still doesn't run and  displays the following errors:
```
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
```

Any ideas please?

Sorry, guys, I still have the same problem, does anyone know what to do? thanks for any help.

---

### Post by bobpaul on 2008-03-13
> **Bandarra said:**
> Sorry, guys, I still have the same problem, does anyone know what to do? thanks for any help.

That error is caused by not having correct graphics drivers installed, as explained by posts 14 and 15 in this thread. Until 'glxinfo | grep direct' returns "direct rendering: Yes" you will continue to experience trouble running this or any other program that requires direct GLX rendering.

If you have an nVidia or ATI graphics card, you can use the Restricted Drivers Manager to install these drivers.

**Edit** Additionally, it seems that error [might appear](http://forums.gentoo.org/viewtopic-t-665453.htm) if your xorg.conf file doesn't list the resolution and color depth phun is attempting to switch to. Phenax from the Gentoo forums recommends turning off shaders in the autoexec.cfg file (located in the phun folder) and checking your xorg.conf. But first, make sure direct rendering is enabled.

---

### Post by Compupaq on 2008-03-21
I've got a question.  How would you make a launcher (shortcut) for it?  Like, what do I put for the command?  I have the 64 bit one btw.

---

### Post by Hal.9000 on 2008-03-21
Create a empty document called 'phun-launcher' in your Phun folder and paste this into it (with the correct paths)
```
export LD_LIBRARY_PATH=/path/to/Phun
/path/to/Phun/phun
```
and then
```
cd /path/to/Phun
chmod +x phun-launcher
```

---

### Post by konr4d on 2008-05-06
so what about this problem ```
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
```

---

### Post by DoriftuEvo on 2008-06-16
Typing

```
~/Desktop/Phun$ LD_LIBRARY_PATH=. ./phun
```

gives me 

```
./phun: line 1: ./phun.bin: cannot execute binary file
```

Simply clicking run on the "phun" file creates a file in the Phun directory named with a bunch of unrecognizable characters and nothing else.  I've installed SDL, but can't get this to run.  I've tried everything in this thread, although understood little.

---

### Post by bobpaul on 2008-07-08
> **DoriftuEvo said:**
> Typing
Simply clicking run on the "phun" file creates a file in the Phun directory named with a bunch of unrecognizable characters and nothing else.  I've installed SDL, but can't get this to run.  I've tried everything in this thread, although understood little.

Hey, I can't seem to duplicate you're error, but I did just re-install phun today on my pc (Phun_beta_4_11_linux64.tgz was the download I grabbed) and got it working again, so let's take a peak.

Please provide the outputs for the following commands:
```
$ uname -a
$ glxinfo | grep direct
$ glxinfo | grep OpenGL
$ ls -la ~/Desktop/Phun
$ aptitude search libsdl | grep ^i
```

---

### Post by itsvan on 2008-08-11
HEY GUYS<,Im a NOOOB NOOB big time,,and i have no idea how to run this PHUN program,,how to install,,do i have to install??? why wont it open,,,all these questions i need some answers,,,and patience,,thank u very much

---

### Post by xen-uno on 2008-08-15
If on 8.04 Hardy, go here ...

[http://getdeb.net/app/Phun](http://getdeb.net/app/Phun)

and at bottom is a 32 & 64 bit link. Click on the appropriate version. On next page, click on link to download. You want to run (vs save) with the debian package installer, which installs 3.5 beta ( 4.22 as of 8/24/08 ). When complete, you should see a Phun entry in Games.

... and it's very cool

---

### Post by brad1138 on 2008-08-24
I have been beating my head against the wall trying to get a launcher to work for Phun (I was able to launch it in Terminal) Thanks for the Dpi link, why isn't all Linux software distributed that way? Linux will never become main stream if you have to try to figure out the other way.

---

### Post by ACleverUsername on 2009-01-08
> **abadtooth said:**
> Just in case anyone else has this problem. 


Phun does not install, all you need to do is make sure the file called "Phun" is allowed to execute via "Right click/Properties/permissions" and make sure "allow executing file as a program"
Then simply right click it and click open/Run.
[URL="http://abadtooths.com/2008/02/19/forget-crayon-physic-hello-phun/"]
http://abadtooths.com/2008/02/19/forget-crayon-physic-hello-phun/[/URL]

apparently thats not all we need to do cause i did that and it doesnt work at all and it does install cause i have an installer and it also isnt working on my computer when i click on it it opens a black window and then the window goes away

---

### Post by Kalimol on 2009-01-17
No Phun for me either, under Intrepid. I checked the direct rendering thing and got a "yes" - 

I get a completely black window that I have to force quit. I tried both the funky-*** folder from the archive and the .deb, which I'm assuming is just a package to extract a copy of said folder into the home directory and tell Gnome how to launch it. I don't get any warnings or errors or missing libraries; I just get an empty window that seems to be trying to do something, like ACU is saying.

Phunny thing is, it works fine under 8.04, just running from that folder. I renamed phun as phun.sh and made it executable, and it worked fine. My graphics card is pitiable and the water effects slow the program down to unusable speeds, even when they're set to simple, but the app runs. I understand that the Hardy version is the most recent, but I know that some people have made it work under Intrepid. How did you do that?

---

### Post by tOfO on 2009-01-19
~$ phun
workdir =  /usr/share/Phun/
Loading language English...
Parsing /usr/share/Phun/autoexec.cfg...
Parsing /usr/share/Phun/config.cfg...
Creating window...
30 resources loaded
Window created.
Prefetching resources
Loaded scene /usr/share/Phun/scenes/welcome.phn
Running program...
Creating window...
122 resources loaded
Window created.
Segmentation fault

---

### Post by ACleverUsername on 2009-01-22
is ubuntu version of phun alot differnet from windows cause all of the versions for windows have worked for me but none of the ubuntu ones work

---

### Post by ACleverUsername on 2009-01-22
> **xen-uno said:**
> If on 8.04 Hardy, go here ...

[http://getdeb.net/app/Phun](http://getdeb.net/app/Phun)

and at bottom is a 32 & 64 bit link. Click on the appropriate version. On next page, click on link to download. You want to run (vs save) with the debian package installer, which installs 3.5 beta ( 4.22 as of 8/24/08 ). When complete, you should see a Phun entry in Games.

... and it's very cool

yes well all of that happened for me but when i open it it is a black screen withe a black mouse with white border and then it goes away???

---

### Post by larry20 on 2009-02-19
> **tOfO said:**
> ~$ phun
workdir =  /usr/share/Phun/
Loading language English...
Parsing /usr/share/Phun/autoexec.cfg...
Parsing /usr/share/Phun/config.cfg...
Creating window...
30 resources loaded
Window created.
Prefetching resources
Loaded scene /usr/share/Phun/scenes/welcome.phn
Running program...
Creating window...
122 resources loaded
Window created.
Segmentation fault

i get the same error
8.10 with version 4.22 i think (got it fromt he gotdeb link)
also running compiz if that makes any difference
help

---

### Post by Malvin on 2009-02-22
same here:
```
illuminatus@thinkbox:~$ phun
workdir =  /usr/share/Phun/
Loading language English...
Parsing /usr/share/Phun/autoexec.cfg...
Parsing /usr/share/Phun/config.cfg...
Creating window...
30 resources loaded
Window created.
Prefetching resources
[here it opens the black window, takes about 2 secs and then vanishes again..]
Loaded scene /usr/share/Phun/scenes/welcome.phn
Running program...
Segmentation fault
illuminatus@thinkbox:~$
```

---

### Post by bengoza on 2009-06-21
**** this game. None of this works. I'm sure it's not worth the effort anyway.

---

### Post by Chronon on 2009-08-28
I just downloaded and got it running today.  Neat game.

My only issue was complaint when running phun from the terminal was about missing libpng.so.3.  So, I did "sudo aptitude install libpng3" and it runs fine.

---

### Post by sceecee on 2009-09-10
Hi guys.
New to ubuntu and loving it :)

Anyways. I found this on another site. 
[http://www.getdeb.net/app/Phun](http://www.getdeb.net/app/Phun)

Ubuntu             Jaunty             32 bits -              [             5.28]("http://www.getdeb.net/release/4553")             
                        Ubuntu             Jaunty             64 bits -              [             5.28]("http://www.getdeb.net/release/4554")             
                        Ubuntu             Hardy             32 bits -              [             4.22]("http://www.getdeb.net/release/3122")             
                        Ubuntu             Hardy             64 bits -              [             4.22]("http://www.getdeb.net/release/3123")             

Fully ready deb packages :) Just download your version, run and the phun will begin :) Works fine.
Tank you, whoever, made this so easy :)
Hope it helps

sceecee

---

### Post by ryecomp on 2009-09-11
Downloading phun from phun original site and run without installing 
fails.. because of ligpng.3.so library... 

So i tried *.deb packages ([http://neacm.fe.up.pt/pub/getdeb/ubuntu/jaunty/ph/phun_5.28-1~getdeb1_i386.deb](http://neacm.fe.up.pt/pub/getdeb/ubuntu/jaunty/ph/phun_5.28-1~getdeb1_i386.deb)) for ubuntu 9.04. 

it installs ok. but it fails. In terminal, it said 
"glxinfo Failed to initialize GEM.  Falling back to classic."... 

Finally it start after i changed /etc/X11/xorg.conf depth from 16 to 24
and restart system (or X)

It is great program..

---

### Post by gardengxc on 2009-09-24
there is a deb version at [http://linux.softpedia.com/progDownload/Phun-Download-36405.html](http://linux.softpedia.com/progDownload/Phun-Download-36405.html). minor graphical glitch but works fine beyond that on my computer.

---

### Post by aelis on 2009-11-25
Hi,
i'm trying to install phun on ubuntu.

I downloaded it
I expanded it in my home directory
I put the permissions of Phun and phun.bin to allow to lauch it as a program

nothing worked

so i tried to lauch it from terminal, i had the following message :
There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

So i tried :
LD_LIBRARY_PATH=. ./phun

and had :
  There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

However those libraries exist in phun's directory.

Maybe someone know how to fix that or, i think i just have to copy phun on the right place in order it finds the lib.

I'm very new in linux, so i need some detailled explainations.

Thanks a lot !

Aelis

---

### Post by Chronon on 2009-11-28
> **aelis said:**
> Hi,
i'm trying to install phun on ubuntu.

I downloaded it
I expanded it in my home directory
I put the permissions of Phun and phun.bin to allow to lauch it as a program

nothing worked

so i tried to lauch it from terminal, i had the following message :
There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

So i tried :
LD_LIBRARY_PATH=. ./phun

and had :
  There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

However those libraries exist in phun's directory.

Maybe someone know how to fix that or, i think i just have to copy phun on the right place in order it finds the lib.

I'm very new in linux, so i need some detailled explainations.

Thanks a lot !

Aelis

You should try installing the packages that it complains about.  The current directory is not automatically part of the path unlike on Windows, so I think Phun is not finding those libraries.  Probably if you copied them to the correct location it would work.  I got it running by installing the appropriate packages via apt-get.

---

### Post by Fastuous on 2010-03-20
@ Aelis:

Dunno if anyone's reading this post anymore but I had the exact same problem as this guy above me, after a lot of searching I found a post right on the Phun website, imagine that! 

[http://www.phunland.com/forum/viewtopic.php?id=6600](http://www.phunland.com/forum/viewtopic.php?id=6600)

So the packages to 'sudo apt-get install' are 'libpng3' and 'libsdl-image1.2'. Once I installed those I executed phun in the terminal and it opened right up. Finally!

Hope this helps others too. But it should at least fix the aforementioned problem.

Tadah!

---

### Post by m.alaa8 on 2010-05-11
May that help?
[http://www.playdeb.net/updates/ubuntu/9.10/?q=phun](http://www.playdeb.net/updates/ubuntu/9.10/?q=phun)

---

### Post by mcativa on 2011-01-07
> **aelis said:**
> Hi,
i'm trying to install phun on ubuntu.

I downloaded it
I expanded it in my home directory
I put the permissions of Phun and phun.bin to allow to lauch it as a program

nothing worked

so i tried to lauch it from terminal, i had the following message :
There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

So i tried :
LD_LIBRARY_PATH=. ./phun

and had :
  There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
    libSDL_image-1.2.so.0 => not found
    libpng.so.3 => not found

However those libraries exist in phun's directory.

Maybe someone know how to fix that or, i think i just have to copy phun on the right place in order it finds the lib.

I'm very new in linux, so i need some detailled explainations.

Thanks a lot !

Aelis

I fixed it installing first the libpng3 package...
```
sudo apt-get install libpng3
```
That installed libpng.so.3 in /usr/lib as a symlink to libpng12.so.0, what was actually missing in my ubuntu 10.04. 
It is part of libpng12-0 package. Install it if you don't have it.
But libpng12.so.0 is actually copied to /lib, and not /usr/lib as expected by the simlink, so you have to create another symlink (or redirect the symlink)
```
cd /usr/lib
sudo ln -s /lib/libpng12.so.0
``` 
and try to run Phun again. It worked for me!

---

