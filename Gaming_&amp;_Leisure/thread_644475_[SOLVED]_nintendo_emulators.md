---
title: "[SOLVED] nintendo emulators"
date: 2007-12-18
forum: Gaming &amp; Leisure
---

### Post by dave00001 on 2007-12-18
Ok, so I've just switched from XP to gutsy, and I'm trying to make my desktop into a movie playing/old skool gaming system.  I've been installing and trying out various emulators from the repositories, and some of them work like a charm, but some (namely nestra and mupen64) don't seem to work.  
I'm a total newbie with linux, but when I install nestra and open it from the terminal, there are no error messages - and I also don't get to see any GUI... and when I install and open mupen 64 as is done in [http://ubuntuforums.org/showthread.php?t=464165&highlight=mupen64](http://ubuntuforums.org/showthread.php?t=464165&highlight=mupen64) , I get an error message...
Has anybody been through this and can help??  I would be very appreciative!!!

PS here is the error message in the terminal window:
dave@dave-desktop:~/Desktop$ sudo sh Mupen64-Script-thegreenblob.sh
--00:22:43--  [http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2)
           => `mupen64-0.5.tar.bz2'
Resolving mupen64.emulation64.com... 62.75.221.236
Connecting to mupen64.emulation64.com|62.75.221.236|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,880,623 (1.8M) [application/x-tar]

 0%  0             --.--K/s                0%  9,811         40.43K/s                2%  39,011        81.40K/s                6%  120,771      168.40K/s               13%  246,248      260.54K/s               19%  365,968      317.90K/s               24%  463,788      341.64K/s               30%  570,368      365.25K/s               36%  688,628      389.80K/s               42%  792,288      400.59K/s               47%  897,512      410.86K/s               52%  993,872      415.82K/s               58%  1,106,292    423.98K/s               65%  1,226,012    435.46K/s               70%  1,329,672    440.03K/s               76%  1,439,172    445.05K/s    ETA 00:00  82%  1,555,972    451.00K/s    ETA 00:00  88%  1,669,852    513.62K/s    ETA 00:00  94%  1,776,432    519.36K/s    ETA 00:00  100% 1,880,623    519.57K/s    ETA 00:00    

00:22:48 (461.75 KB/s) - `mupen64-0.5.tar.bz2' saved [1880623/1880623]

mupen64-0.5/
mupen64-0.5/mupen64
mupen64-0.5/mupen64.ini
mupen64-0.5/whatsnew.txt
mupen64-0.5/save/
mupen64-0.5/save/empty
mupen64-0.5/doc/
mupen64-0.5/doc/readme.pdf
mupen64-0.5/doc/HiRezTexture.txt
mupen64-0.5/lang/
mupen64-0.5/lang/catalan.lng
mupen64-0.5/lang/pt_BR.lng
mupen64-0.5/lang/german.lng
mupen64-0.5/lang/spanish.lng
mupen64-0.5/lang/dutch.lng
mupen64-0.5/lang/italian.lng
mupen64-0.5/lang/english.lng
mupen64-0.5/lang/french.lng
mupen64-0.5/plugins/
mupen64-0.5/plugins/blight_input.so
mupen64-0.5/plugins/dummyaudio.so
mupen64-0.5/plugins/glN64.so
mupen64-0.5/plugins/jttl_audio.so
mupen64-0.5/plugins/mupen64_audio.so
mupen64-0.5/plugins/mupen64_input.so
mupen64-0.5/plugins/mupen64_soft_gfx.so
mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so
mupen64-0.5/plugins/ricevideo.so
mupen64-0.5/plugins/RiceVideo6.1.0.ini
mupen64-0.5/plugins/Glide64.so
mupen64-0.5/plugins/Glide64.ini
mupen64-0.5/plugins/tr64gl.so
mupen64-0.5/jttl_audio.conf
mupen64-0.5/mupen64_icon.png
tee: /usr/local/bin/mupen64: No such file or directory
#!/bin/bash 
/usr/local/games/mupen64-0.5/mupen64
chmod: cannot access `/usr/local/bin/mupen64': No such file or directory
rm: cannot remove `mupen64-0.5.tar.bz2': No such file or directory
[Desktop Entry]
Type=Application
Name=Mupen64
Exec=mupen64
Comment=An N64 Emulator.
Icon=/usr/local/games/mupen64-0.5/mupen64_icon.png
Terminal=false
Categories=Application;Game;ActionGame;GameAction;ActionGames;GamesAction;
dave@dave-desktop:~/Desktop$ mupen64
bash: mupen64: command not found

Please Help!

---

### Post by geekygirl on 2008-01-13
I installed Mupen64 like this:

I downloaded the file from the Mupen64 website [[COLOR="Blue"]here[/COLOR]]("http://mupen64.emulation64.com/down.htm")

Extracted the tar file into a folder in my Home folder - just right click and use the  'extract here' option.

To run it you can either type in terminal:

```
cd /home/<username>/mupen64-0.5

./mupen64
```

or you can create a launcher on the desktop like this:

Right click on your desktop

Select Create Launcher option in menu

Leave Type as Application

Name: Well anything you like - I called it Mupen 64

Command: Enter```
 /home/<your username>/mupen64-0.5/./mupen64
```

You can then set your own icon by clicking on the icon box in the 'Create Launcher' dialog box

For a menu launcher you need to do this:

```
cd /home/username/mupen64-0.5/./mupen64

sudo mv mupen64_icon.png /usr/share/pixmaps/

gksudo gedit /usr/share/applications/mupen.desktop
```

copy and paste this editing your username and file path as required:

```
[Desktop Entry]
Encoding=UTF-8
Name=Mupen64
Exec=/home/<insert your username here>/mupen64-0.5/./mupen64
Icon=mupen64_icon.png
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false

```

Thats pretty much what the script you are trying to use will do, but I know this method works and thats how I have Mupen running on my Gutsy box!

:)

---

### Post by acoustibop on 2008-01-13
I think the reason is that this folder, ```
/usr/local/bin/mupen64
``` should be created but I don't see a line in your script to do this, dave00001.  So every time the script needs to access it, you get an error.

You could try creating the folder first.  Or, as geekygirl says, just download the .tar.bz2 file, tar it in your Home folder and run it from there.

---

### Post by geekygirl on 2008-01-13
Yeah I think the script does want to install in the bin folder, however the instructions from Mupen suggest extracting the folder into your home drive as it wasnt written to be installed as such :)

As long as you can get it working thats the main thing!

---

### Post by acoustibop on 2008-01-13
I agree, geekygirl, it avoids a lot of issues just to put the folder in your Home folder.  I was just pointing out that, from the results from dave00001's script, it looks like it's trying to move files to /usr/local/bin/mupen64 and then modify it without, apparently, having created it first.  So if dave00001 wants to run that script successfully, the easiest way might be to create the folder first.

---

### Post by dave00001 on 2008-01-18
Thanks, geekygirl... Now I know how to launch applications from the terminal!!! So, I can call the Mupen64 GUI now, but when I try to load ROMS, there seems to be complications....  The program seems to be loading the roms, but afterwards Mupen64 freezes and I get nothing!  I am loading files of type .z64 and .v64.  I'm not sure why???

By the way, thanks for the response on an old thread and I am very appreciative of your help!!  ;)

---

### Post by acoustibop on 2008-01-18
What error messages do you get in the terminal, dave00001?  What plugins are you using and how have you configured them?

---

### Post by Dark Aspect on 2008-01-18
> **dave00001 said:**
> Thanks, geekygirl... Now I know how to launch applications from the terminal!!! So, I can call the Mupen64 GUI now, but when I try to load ROMS, there seems to be complications....  The program seems to be loading the roms, but afterwards Mupen64 freezes and I get nothing!  I am loading files of type .z64 and .v64.  I'm not sure why???

Not to interrupt in the thread but are you using Ubuntu 64-bit by any chance.I had the same same problem with Mupen64 on my system and it was because Dynamic Recompiler mode (default) only works on x86.Open Mupen64 goto options/configure and try setting the CPU core as a interpreter.Yes I realize your going to lose some FPS by doing this but I have a slightly powerful computer (No SLI sadly) and most games appear to run decent though Mupen64.

---

### Post by dave00001 on 2008-01-18
Thanks for the replies...

Acoustibop:  here is the terminal error messages:

dave@dave-desktop:~/mupen64-0.5$ ./mupen64
Couldn't load plugin '/home/dave/mupen64-0.5/./plugins/mupen64_hle_rsp_azimer.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/dave/mupen64-0.5/./plugins/Glide64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/dave/mupen64-0.5/./plugins/mupen64_soft_gfx.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/dave/mupen64-0.5/./plugins/glN64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/dave/mupen64-0.5/./plugins/ricevideo.so': libstdc++.so.5: cannot open shared object file: No such file or directory


So, I am guessing it is an issue of plugins.. but, since I am pretty new at this, I don't exactly know how to get and install them - it would be much easier if they came pre-installed!

DarkAspect:  This may sound ridiculous, but I really don't know whether I am running a 32 or 64 bit system...  I have a Pentium 4 processor (2.00 GHz) running "kernel linux 2.6.22-16-generic" does this help at all??

Again, thanks for your help and patience - I'm still on the learning curve ;)

---

### Post by DoktorSeven on 2008-01-18
If you have a Pentium4, you're running 32bit, no doubt.  You would have to have a new processor and a specific 64-bit version of Ubuntu to be running 64-bit.

As for the errors: searching for that library (libstdc++.so.5) using **apt-file** (sudo apt-get install apt-file && sudo apt-file update) gives me:

```
$ apt-file search libstdc++.so.5
libstdc++5: usr/lib/libstdc++.so.5
(more duplicates and other stuff removed)

```

So try doing **sudo apt-get install libstdc++5** and see if that fixes the problem.

---

### Post by dave00001 on 2008-01-18
Thanks, DoktorSeven, now I think I am almost there...

I can now successfully load roms, but when I try to play them, I get an error message:

memory initialized
[blight's SDL input plugin]: Couldn't open blight_input.conf for reading: No such file or directory
[blight's SDL input plugin]: version 0.0.10 initialized.
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
(EE) Error setting videomode 640x480: Couldn't find matching GLX visual

(mupen64:7532): GLib-WARNING **: g_main_context_prepare(): main loop already active in another thread


I believe this is a resolution problem??  Could be because I have switched my computer monitor for a CRT television, but my resolution is 800x600 @ 61 Hz... so maybe not... 
If anyone has any insight into this it would be great!!

---

### Post by DoktorSeven on 2008-01-18
> Couldn't find matching GLX visual

Sounds like a 3d issue to me.  Do you have direct rendering enabled for your card?

```
glxinfo | grep direct
```
Should return:
**direct rendering: Yes**

If it returns No, you need to look into how to enable 3d for your card.  If you have an nvidia or ATi card it should be as simple as running the restricted drivers manager (search for details).  If not, what card do you have?  I'm not sure on details to enable 3d on other cards, so you might do a search.

Also, good idea to disable 3d desktop if you have it enabled when running 3d games and emulators.

---

### Post by dave00001 on 2008-01-19
Hmmm...  I'm pretty sure I don't have direct rendering, looking at my terminal message:

dave@dave-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I'll try to look into enabling 3d on my card - it's an NVIDIA GeForce 6200 OC, and I have the right drivers, but once again if you have any suggestions I would be very appreciative!

---

### Post by DoktorSeven on 2008-01-19
Since you have an nvidia card, running the restricted drivers manager in any recent version of Ubuntu should be adequate.  (If you don't have Ubuntu, or an old version without the restricted drivers manager, you'll need to look up how to do that...)

---

### Post by Dark Aspect on 2008-01-19
> **dave00001 said:**
> Hmmm...  I'm pretty sure I don't have direct rendering, looking at my terminal message:

dave@dave-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I'll try to look into enabling 3d on my card - it's an NVIDIA GeForce 6200 OC, and I have the right drivers, but once again if you have any suggestions I would be very appreciative!

Um I have an Nvidia GeForce 6800 GS and while most people use the restricted drivers manager I found the command line way to be as about as easy:

> sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable

Seems to work for the last two Ubuntu releases.If this does not work IDK how to fix it sry.

---

### Post by dave00001 on 2008-01-21
So, I've enabled my nvidia-glx-new driver via the restricted drivers manager, and restarted, but I still get the same problem:  No direct rendering, and the same error message.  Kind of frustrating, but any help would be great!  Thanks all for your help so far...

---

### Post by Bakhman on 2008-01-21
I tried Geekygirl's method, but when I try to extract the file to my home folder it gives me:

An error occurred while extracting files.
End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/behrang/Downloads/mupen64 0.5.1.exe or
        /home/behrang/Downloads/mupen64 0.5.1.exe.zip, and cannot find /home/behrang/Downloads/mupen64 0.5.1.exe.ZIP, period.

??? I'm using Gutsy and it'd be nice to have some games on here...

---

### Post by dave00001 on 2008-01-31
Ok, so I FINALLY got it to work:  

I had to re-install my nvidia driver, but after doing this from the command line via Dark Aspect's method, I noticed that my xorg.conf was not being correctly re-written... (basically I just had to change "nv" to "nvidia") so now it works flawlessly!  I do, however now have issues with my resolution, it's stuck at 1280 x 1024, but this is a different issue, which I'll try my luck in another forum.  Thanks all for your help!

---

