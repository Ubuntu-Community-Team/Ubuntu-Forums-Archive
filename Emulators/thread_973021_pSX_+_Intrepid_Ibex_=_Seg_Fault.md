---
title: "pSX + Intrepid Ibex = Seg Fault"
date: 2008-11-06
forum: Emulators
---

### Post by cisforcojo on 2008-11-06
Anyone tried running pSX in Ibex?

Here's what I get:
> $ ./pSX 
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

---

### Post by lifestream on 2008-11-06
Me too! 
Maybe we should look at line 215 on sound.cpp :P
Though I'm curious... why is it looking at the sources? O.o


> [src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

Happens right after I tell  it which bios to pick. If the bios is placed on the correct spot (pSX/bios folder) it still gives seg fault

---

### Post by dfreer on 2008-11-06
Try removing pulseaudio:
```
EDITED
```

---

### Post by lifestream on 2008-11-06
*chews on nails*
Quite a drastic solution, isn't it?
*gulp*
*tries anyway*
I really want to play my games >_> My TV broke, so I can't use my console anymore.

---

### Post by Grishka on 2008-11-06
> **dfreer said:**
> Try removing pulseaudio:
```
sudo apt-get remove pulseaudio*
```

that's not necessary. killall pulseaudio will suffice. I only had to do this once and fiddle a bit with pSX sound settings, pSX runs fine now, even with pulseaudio on after reboot.

---

### Post by lifestream on 2008-11-06
Thank you both!
It really worked!
Now I can play Crash Bandicoot after a month without TV! :D
My boyfriend is going to have to wait for dinner tonight :P
*Cheers!*

---

### Post by lifestream on 2008-11-07
Yeah, definitely don't sudo apt-get remove pulseaudio*
It will make you unable to log in, even if you remove it from Sessions, and even as a new user.

killall  pulseaudio will suffice.

:P

---

### Post by dfreer on 2008-11-07
Edited earlier post. I've only tested Ubuntu Intrepid via Live CD, so I never noticed the rebooting issue, and stopping the pulseaudio daemon didn't seem to solve the problem. It appears that even after sending the pulseaudio daemon a stop signal pulseaudio continues to run, it may be just a bug in the Live CD.

See if this package or the script (whichever you feel like using) fixes pSX for you:
[http://ubuntuforums.org/showpost.php?p=6127662&postcount=246](http://ubuntuforums.org/showpost.php?p=6127662&postcount=246)

All I did was create a bash script to kill pulseaudio before launching pSX, then restart pulseaudio afterwards. Hopefully this should help people :D

---

### Post by zero777zero on 2008-11-07
it would be nice if there was a proper fix for this...

---

### Post by dtuza on 2008-11-18
Oddly enough, the 32bit Intrepid .deb file at

[http://ubuntuforums.org/showpost.php...&postcount=246](http://ubuntuforums.org/showpost.php...&postcount=246)

doesn't seem to work for me, in that it doesn't seem to correctly kill pulseaudio.  When I run the executable, my system seems to just jog in place for a moment or two, to no effect.  Running it (the new executable) in a terminal produces the same error as before:

$ ./pSX
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

and using killall pulseaudio fixes the issue, as mentioned earlier in this thread.  Any ideas?

---

### Post by dfreer on 2008-11-19
BTW, your link doesn't work, but I'm assuming it's my packages since ATM I'm the only one creating .deb packages for pSX that I'm aware of. It's a bash script in /usr/bin, and it uses gksu/do killall pulseaudio.

I might have messed something up in the script, IDK. Try fiddling with it if you can, I'm a bit busy with a new job but I'll try to help out if I can.

---

### Post by dtuza on 2008-11-19
> **dfreer said:**
> BTW, your link doesn't work, but I'm assuming it's my packages since ATM I'm the only one creating .deb packages for pSX that I'm aware of. It's a bash script in /usr/bin, and it uses gksu/do killall pulseaudio.

I might have messed something up in the script, IDK. Try fiddling with it if you can, I'm a bit busy with a new job but I'll try to help out if I can.

Nah you're right.  Works fine that way - I assumed everything had been compiled back into the executable.  Cheers, and thanks again.

---

### Post by Lunatico_22 on 2008-11-22
I can't run pSX on Intrepid 64 bit... When trying to launch it, it displays: 

libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

I have installed the libgtkglext1 package and the file do appear in /usr/lib

I used pSX without problems on hardy 64 bit, I dont know whats going on

---

### Post by dfreer on 2008-11-22
pSX is a 32-bit program, which means you need to install 32-bit libraries in order for it to run. 32-bit binaries = 32-bit libraries, 64-bit binaries = 64-bit libraries. 

You can see which libraries a program needs in order to run using the ldd command in terminal. Generally, the shell is also smart enough to tell you which library you are missing (which is why you got the error message you did), but does not tell you whether any more libraries are missing, or whether the libraries missing need to be 32-bit or 64-bit.

When you install the package libgtkglext1, if you are on a 64-bit system, you get the 64-bit libraries only. So simply installing libgtkglext1 will not help (it should already have been installed anyways I'm pretty sure).

There's several things you can do:
(1). Install the package I've created that contains the 32-bit libraries you need installed in the correct spot: [http://ubuntuforums.org/attachment.php?attachmentid=91607&d=1226105184](http://ubuntuforums.org/attachment.php?attachmentid=91607&d=1226105184)
(2). Download the 32-bit version of the libgtkglext1 package from [http://packages.ubuntu.com](http://packages.ubuntu.com), and extract the 32-bit libraries from it and install them somewhere the system can find them (/usr/lib32/ is the default system-wide location for 32-bit libraries).
(3). Use get-libs, which uses some intelligent scripting to determine which libraries a binary needs to run, and then grabs them and installs them. From what I hear the program works well, but I do not know whether or not it performs any sort of "tracking", for removal/upgrading of libraries.

---

### Post by Lunatico_22 on 2008-11-26
Nice, now it works... Thanks a lot!

---

### Post by dkrus on 2008-11-28
the psx is working, but when I go to chose incert cd image or any other choice from file it just flickers in and out and cant be read, Is there anything that can be for this? I'm running 8.10 32 bit

---

### Post by Grishka on 2008-11-28
> **dkrus said:**
> the psx is working, but when I go to chose incert cd image or any other choice from file it just flickers in and out and cant be read, Is there anything that can be for this? I'm running 8.10 32 bit

looks like you don't have a BIOS file configured. if that's not it, run psx from the terminal, and check the errors.

---

### Post by dkrus on 2008-11-28
I'm pretty sure the bios is fine, I ran it from terminal and only sound overrun showed up.

---

### Post by Grishka on 2008-11-29
> **dkrus said:**
> I'm pretty sure the bios is fine, I ran it from terminal and only sound overrun showed up.

try doing 'killall pulseaudio' before running psx.

---

### Post by dkrus on 2008-11-29
I use the script that dfreer made to kill pulseaudio then launches psx

---

### Post by supercompman on 2008-12-17
A different, and in my opinion a nicer solution to the pulseaudio problem is to edit a configuration file... Open a terminal and type:

sudo gedit /etc/pulse/default.pa

I took the section that looks like this:

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

and commented it out so that it looks like this:

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

and took the section that looked like this:

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

and uncommented the alsa sink and source:

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink
load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

Save the changes and reboot. I haven't had any problems with pSX since and all other applications using sound seem unaffected as far as I can tell.

---

### Post by supercompman on 2008-12-18
Never mind about my previous post... I was actually causing pulseaudio to fail to load, which I might as well have been turning pulseaudio off entirely or killing as suggested previously.

---

### Post by Moncho-on-the-Mac on 2009-01-01
Hey all, long-time lurker posting my experience here.

I'm running Intrepid on an older Dell Desktop model (I'm thinking it's possibly a Dimension or an Inspiron, not sure), and I was having the same issues with pSX + pulseaudio.

Interestingly enough, killall-ing pulseaudio would also kill audio output on Firefox for the remainder of my session. To regain audio for YouTube, I'd have to log out and log back in.

But by tweaking with the sound options on pSX, I think I managed to get a fix on this. I specified the device my Dell seems to like (VIA 8237), and it ceased giving me problems afterwards. I was able to launch pSX after startup with no problems, and Firefox audio remained.

Hopefully this'll be of some assistance.

-Moncho

---

### Post by wiebeest on 2009-02-23
Maybe a tab off topic, but why go over all this hassle? You can use ePSXe though WINE. Works perfectly. No sound problems. And much more graphical enhancing output settings. Just a thought.

---

### Post by Jello B. on 2010-10-22
In 10.10 you have to add
```
autospawn = no
```
to client.conf in the .pulse folder in your home before you can killall pulseaudio

---

### Post by kistina on 2010-11-05
I still get the segmentation fault even after changing autospawn to no.

---

### Post by bafn on 2011-12-02
I dont know if I all of You having seg fault have ATI graphic cards, but I do (Mobility Radeon HD 5470) and I have found dependence between fglrx drivers and pSX crashing. When I have fglrx installed, pSX won't run. And when I uninstall them, pSX runs, but flickers when something else on the desktop is happening or moving or simply when I move pSX window.

Of course when I reboot the system graphics are dead, so I must install fglrx again. I hope it's because of catalyst being old (I have 10.2 or something), I'll try with new version now (11.11), hope it works. Or maybe You have another solution for this? Do I have to install ATI drivers or the ones proposed by Ubuntu? (I don't know if pSX works with the Ubuntu ones, though). 

I'll try with catalyst 11.11 and tell You how it worked.

---

