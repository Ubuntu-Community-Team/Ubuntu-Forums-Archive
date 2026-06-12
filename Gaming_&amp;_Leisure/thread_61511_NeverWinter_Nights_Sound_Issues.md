---
title: "NeverWinter Nights Sound Issues"
date: 2005-09-01
forum: Gaming &amp; Leisure
---

### Post by dducko3 on 2005-09-01
I am haveing issues with NWN and sound, Sound works almost everywhere but in NWN, I have system sounds, I can play music, The Gnome games work fine,. Firefox seems to have issues too, (not so worried about that, just hear for refference). 

I followed the tutorials for installing NWN on linux over on the Bioware boards.  When I run it, no sound and when I go into the Game options it doesnt appear as if there is even a sound device for it to work with.  I have tried different things like "killall esd" before starting it but with no luck.   I would appreciate any help I am given.

---

### Post by Perfect Storm on 2005-09-01
I don't know what they say on bioware, but when I install NWN I use this site and its programs. Perhaps it helps you :) : [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

---

### Post by art2003 on 2005-11-27
I had the same problem and fixed it easily.

The linux client comes with its own sdl library just in case you don't have one.

Well that one didn't work for me but the ubuntu one works fine.

so...
in your neverwinternights folder
open nwn with your favourite editor and replace the text there with this:

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
# note that I have modified the next line to use the ubuntu sdl library!
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

esdctl off
sleep 2
./nwmain $@
esdctl on

``` 


note that in the code the third export line h

---

### Post by blacklantern on 2006-01-12
*bump*

I have the exact same problem that dducko3 had, and I copied the above script into my nwn file. However, I still have no sound, and NWN doesn't recognize any sound device.

---

### Post by AngryKidJoe on 2006-06-24
I get this error with that change:
```
akj@angry-penguin:~/nwn$ ./nwn
./nwn: line 13: esdctl: command not found
./nwmain: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
./nwn: line 16: esdctl: command not found

```
Like a moron, I forgot to make a backup and NWN won't even boot up now.

---

### Post by art2003 on 2006-06-26
find where the library is on your system
find / -name libsdl*

and then copy it to your NWN directory and should be fine.

(if there is already a library with that name in your NWN directory overwrite it with the one from your system)

---

### Post by TomPurnell on 2007-02-25
I also had no sound on my 64bit system. Changing the nwn script produced the missing libSDL error, due to the game requiring a 32bit version of the lib. I fixed this by installing the ia32-libs-sdl package, now I have sound :)

---

### Post by gldvxx on 2007-03-11
pasting this text into my nwn script fixed an issue i was having as well.  after i installed amarok i kept getting the infamous mcop error when i tried to run nwn!  (i'm running gnome) 

mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /root/.kde/socket-bobdobalina.
can't create mcop directory

one suggestion had been to set SDL_AUTODRIVER to esd, but that only caused really bad sound degradation after i played neverwinter nights for awhile.  i kept having to restart nwn.  

the only issue i have with this script is i get this error message:
nwn: line 13: esdctl: command not found
nwn: line 16: esdctl: command not found

but other than that, the game works as well as it did when i first started playing it on ubuntu!  yay!

---

### Post by danlee on 2008-03-02
[quote="gldvxx"]the only issue i have with this script is i get this error message:
nwn: line 13: esdctl: command not found
nwn: line 16: esdctl: command not found[/quote]
You need to install the "esound-clients" package.
```
sudo apt-get install esound-clients
```
Thanks, this fixed the scratchy audio on my 64bit debian :)

---

### Post by SandmanXC on 2008-04-15
Thanks, the paste did help :D

---

### Post by scrawl on 2008-06-22
I also get an output like this:
nwn: line 13: esdctl: command not found
nwn: line 16: esdctl: command not found

But nwn starts and everything works fine. Thanks :)

---

### Post by soupmonster on 2009-04-10
Hi guys,

I've tried all the suggested solutions for this problem, and none of them seem to work for me. I'm trying to run NWN on Jaunty Beta, but I do **not** get any error messages at the console when launching the game. 

I tried removing lib from the LD_LIBRARY_PATH in order to make the game use the Ubuntu library. - Game loads, but no sound.

I tried symlinking the Ubuntu library from within the lib folder of NWN. - Again, game loads, no sound.

I tried copying the Ubuntu library to the lib folder. - Still no luck.

I've also tried apt-getting the libSDL pulseauido plugin, and setting that as the audio driver, but no luck. Other games using libSDL seem to play audio fine.

Not really sure what to try next.

---

### Post by Brian Vaughan on 2010-04-07
NWN worked for me in the past, but I was surprised to find that the sound had stopped working since the last time I tried it (which was probably a year or so ago).

I found I could get the sound working, simply by commenting out the line, "export SDL_AUDIODRIVER=alsa". So, the script is now as follows:
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
#export SDL_AUDIODRIVER=alsa

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
./nwmain $@
```

---

### Post by alexandrius on 2010-08-12
> **Brian Vaughan said:**
> NWN worked for me in the past, but I was surprised to find that the sound had stopped working since the last time I tried it (which was probably a year or so ago).

I found I could get the sound working, simply by commenting out the line, "export SDL_AUDIODRIVER=alsa". So, the script is now as follows:
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
#export SDL_AUDIODRIVER=alsa

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
./nwmain $@
```
dude thanks that worked!

---

### Post by Lady_Dark_Kitten on 2010-09-17
I also have no sound, the autorun menu has sound but the actual game doesn't. I follow that up by saying I did not use the Linux installer, I'm on Ubuntu 10.4 and could not for the life of me get the linux installers (any of them) to work properly. So since my actual dvdrom is not working I created a drive in media linked that to wine and mounted a NWN Diamond iso, the game installed perfectly. Everything else works like a champ but I have no sound. Since I'm not running it with the linux files is there anything I can do or am I stuck looping the audio through my music player?

---

### Post by woodrobin on 2010-09-21
> **Lady_Dark_Kitten said:**
> I also have no sound, the autorun menu has sound but the actual game doesn't. I follow that up by saying I did not use the Linux installer, I'm on Ubuntu 10.4 and could not for the life of me get the linux installers (any of them) to work properly. So since my actual dvdrom is not working I created a drive in media linked that to wine and mounted a NWN Diamond iso, the game installed perfectly. Everything else works like a champ but I have no sound. Since I'm not running it with the linux files is there anything I can do or am I stuck looping the audio through my music player?

This should work regardless of the Windows/Linux file use, since the main difference is an alteration to an SDL sound card setting:

[http://nectarius.net/2007/08/22/puzzle-pirates-and-nwn-sound/](http://nectarius.net/2007/08/22/puzzle-pirates-and-nwn-sound/)

Here is the code that should be used in place of the existing nwn file (note that the text /GAMEINSTALLPATH/ should be changed to the directory in which you have Neverwinter Nights installed -- this is a convenience fix to allow easier launches, not the sound fix per se):

```
#!/bin/sh cd /GAMEINSTALLPATH/
 # This adds a variable to make sound  work properly. NWN doesn't work with
# select() function in the SDL sound library properly.
# I think this means it doesn't know how to choose which sound card to use in
# some setups.
export SDL_DSP_NOSELECT=1
 # This script runs Neverwinter Nights from the current directory
 export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
 # If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
 ./nwmain $@
```This fixed audio for me after an update seemed to cause it to stop working today, and cleared up the error messages I had previously been seeing even on successful runs, as well.

---

### Post by stackmanpf77 on 2012-10-09
I too am having a great deal of difficulty getting sounds active in NWN (platinum CD install)...
I've altered the nwn run script in every way I've found on this, and many other forums, all to no avail.
I Did get it working for about 12 hours with the addition of the 

export SDL_AUDIODRIVERS=alsa

command line, but did a system restart and it has gone kaput.
Nothing I have tried since has had any effect whatsoever besides turning my hair grey.

Currently, my nwn run script reads as - 

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
#export SDL_AUDIODRIVERS=alsa

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@

and nothing sound-wise...
(sound aside, game runs flawlessly, no high res screen flutter/flicker, no mouse lag, movies work (sans sound)

any help would be appreciated.

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

