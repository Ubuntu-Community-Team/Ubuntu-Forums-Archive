---
title: "No sound in Enemy Territory"
date: 2005-06-10
forum: Gaming &amp; Leisure
---

### Post by timelord726 on 2005-06-10
Hi all! I'm having a problem with my sound on Ubuntu. This is a reasonably fresh install, but I have been running for a day or two now so I've customized some things to my liking. The only thing I've done with sound, though, is applied Gandalf and Varunus's "HOWTO: Hear multiple sounds using Both ESD & ALSA" [here]("http://ubuntuforums.org/showthread.php?t=32063"). Everything is working very well right now for the most part, but one thing I just cannot fix is Enemy Territory's sound. I get no sound at all in the entire game.

My **Multimedia Systems Selector** is configured to use ALSA for both sink and source. Everything else is working, and ESD and ALSA play together nicely pretty much all the time.

I have seen this:
 ```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```
But it tells me that:
 ```
bash: /proc/asound/card0/pcm0p/oss: No such file or directory
bash: /proc/asound/card0/pcm0p/oss: No such file or directory
``` 
Can anyone provide some pointers?  Thanks!

---

### Post by professor_chaos on 2005-06-10
Yes, I tried several things including and in addition to what you had mentioned.
What I believe worked for me was to install "libsdl1.2debian-all" and or disabling surround sound via alsa settings. 
Give them a try.
Sorry I can't be more enlightening.
Good luck.

After all the work to get sound working, I didn't really think the game was that great. 
I was really RNG (run and gun) and really way to fast to even slightly resemble reality. But then again, it's a video game and not reality. Whatever.....

---

### Post by timelord726 on 2005-06-11
I've played it before, and it's fun for me.  Not the best game I've played, oh no, but it's a free FPS for Linux.  I can't complain.

I'll try the solutions you suggest when I get back to my home computer, but I think I've already tried those.  I could be wrong, though, and I'll let you know.

---

### Post by fireedo on 2005-06-12
[QUOTE=professor_chaos]Yes, I tried several things including and in addition to what you had mentioned.
What I believe worked for me was to install "libsdl1.2debian-all" and or disabling surround sound via alsa settings. 
Give them a try.
Sorry I can't be more enlightening.
Good luck.

After all the work to get sound working, I didn't really think the game was that great. 
I was really RNG (run and gun) and really way to fast to even slightly resemble reality. But then again, it's a video game and not reality. Whatever.....[/QUOTE]
 how to disabling sorround sound via alsa setting?

---

### Post by Watcher on 2005-06-13
[QUOTE=professor_chaos]Yes, I tried several things including and in addition to what you had mentioned.
What I believe worked for me was to install "libsdl1.2debian-all" and or disabling surround sound via alsa settings. 
Give them a try.
Sorry I can't be more enlightening.
Good luck.

After all the work to get sound working, I didn't really think the game was that great. 
I was really RNG (run and gun) and really way to fast to even slightly resemble reality. But then again, it's a video game and not reality. Whatever.....[/QUOTE]
I have the same problem as the first poster, tried your solution, but i don't really know how to disable the surround sound, unless you mean disabeling it, using alsamixer?

Anyway if anyone has an idea how to solve this please let me know, I really don't want to switch back to windows to play this game :)

---

### Post by elocal on 2005-06-13
I think you guys just have to make sure that alsa oss emulation modules are loaded.

Run "sudo lsmod" and check if, if I remember correctly, that "snd_seq_oss" "snd_mixer_oss" "snd_pcm_oss", are listed.  

If they are not in the list run the command "sudo modprobe name_of_module" substituting "name_of_module" with the name of the module that is not loaded, if sound works afterwards add the name of the modules that weren't loaded to /etc/modules.

good luck

---

### Post by Watcher on 2005-06-14
Great, let me check that now  :)

---

### Post by timelord726 on 2005-06-14
Worked like a charm for me!  All my games and applications have sound running flawlessly now!  Thank you so much! :D

---

### Post by ubuntu_demon on 2005-06-15
edit :

I had problems with ET sound. After sudo apt-get install alsa-oss ....switching to alsa and a reboot it worked!

---

### Post by timelord726 on 2005-06-15
The only advice I can offer is that I had to run:

$ sudo modprobe snd_seq_oss
$ sudo modprobe snd_mixer_oss
$ sudo modprobe snd_pcm_oss

before my sound worked.  Did you try all three?  Because your post makes it sound like you only tried the first one.

I hope that's able to help!

---

### Post by elocal on 2005-06-15
[QUOTE=timelord726]Worked like a charm for me!  All my games and applications have sound running flawlessly now!  Thank you so much! :D[/QUOTE]
 You're welcome.  

Now, I just have to wait from my 6600GT to get back from RMA so I can play games again, I have basically no good video card now... cant wait! now that vacation is about to begin...

---

### Post by timelord726 on 2005-06-15
My vacation's already started, but then again, I have a good video card too, so I can't complain.  :grin:

---

### Post by Watcher on 2005-06-15
[QUOTE=timelord726]The only advice I can offer is that I had to run:

$ sudo modprobe snd_seq_oss
$ sudo modprobe snd_mixer_oss
$ sudo modprobe snd_pcm_oss

before my sound worked.  Did you try all three?  Because your post makes it sound like you only tried the first one.

I hope that's able to help![/QUOTE]

I just tried this, still no sound in ET :( don't really know what is wrong (and I'm a linux noob so I'm not really keen on snooping around in a lot of config files)

Anybody have some other solutions? Or want me to post certain logfiles, just ask.

EDIT: perhaps this could help some people
> ------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/bernard/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/bernard/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/bernard/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa5ccdf40
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---

---

### Post by elocal on 2005-06-16
[QUOTE=Watcher]I just tried this, still no sound in ET :( don't really know what is wrong (and I'm a linux noob so I'm not really keen on snooping around in a lot of config files)

Anybody have some other solutions? Or want me to post certain logfiles, just ask.

EDIT: perhaps this could help some people[/QUOTE]
 Can you cat or hexdump /dev/dsp??? try "sudo cat /dev/dsp" or "sudo hexdump /dev/dsp" and tell me if it gives you any error like /dev/dsp does not exist...

---

### Post by Watcher on 2005-06-16
Ok when i do the hexdump thing i get this

> bernard@bernardtux:~$ sudo hexdump /dev/dsp
Password:
0000000 8181 8181 8181 8181 8181 8181 8181 8181
*



with other i just get a load of little boxes on my screen :s nothing more and just won't stop showing up

---

### Post by Watcher on 2005-06-16
[QUOTE=Watcher]Ok when i do the hexdump thing i get this



with other i just get a load of little boxes on my screen :s nothing more and just won't stop showing up[/QUOTE]
 I found a working solution in the ET thread on the warthy forum :)

Now i can finally enjoy nice sound in ET

> Troubleshooting
Sound Issues
I found that sound did not work for my setup, giving me the following error:
/dev/dsp: Input/output error Could not mmap /dev/dsp
To resolve this issue I simply typed from root terminal the following:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by pepolez on 2005-10-20
Open a terminal (as current user) and type:
```
killall esd
```
This will stop esd from taking over the sound device, next, type:
```
artsd
```
then open a new terminal (leaving the artsd command to run) to run et:
```
artsdsp -m et
```
replace et in last command with command used to execute enemy territory (although it usually is 'et'). this worked for me when using an alsa mixer, although the sound was quite chunky on my onboard sound :)

EDIT: you'll have to find a way to restart escd after playing et otherwise sound wont work in most apps until you reboot

---

### Post by yekim on 2007-08-25
All,

I am having a very similar sound problem with ET in Ubuntu Fiery Fox.  Here is what I've tried:

```
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

But it returns

```
bash: /proc/asound/card0/pcm0p/oss: Permission denied

```

I've tried making the following boot script per another post:

```
#!/bin/bash
gksudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
gksudo echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
et
esd
exit 0
```

But when ET starts I get the following error:

```
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

```

So I checked lsmod and I do see:

```
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

which look to be all the necessary things.

I did sudo apt-get install alsa-oss but I already had this.

I tried sudo hexdump /dev/dsp and got a similar message to the other user, which was not anything like "does not exist."

I'm really stuck here!  Any help appreciated.

Yek

---

### Post by pirate3113 on 2007-09-07
i ran into either the same problem, or a very similar one.  the best explaination i could figure out what the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" command had to be run after you were root, instead of becoming root in the command.  

try this:

sudo su

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

also, for some reason whenever i reistall my os i have to run:  "sudo passwd root" and re-type my password cause my "su" command doesnt work till i do that.  hope it helps.

---

### Post by Juggercat on 2008-11-19
That last one worked for me, thx guys!

---

### Post by epitaph on 2008-11-20
For me, a lot of the tricks used above had unwanted side effects, such as no other devices being able to output to /dev/dsp and so forth. The solution I chose was to use SDL sound with et-sdl-sound.

[http://nullkey.ath.cx/et-sdl-sound/](http://nullkey.ath.cx/et-sdl-sound/)

> et-sdl-sound provides SDL-based replacement for deprecated OSS-based sound systems of Enemy Territory, Return to Castle Wolfenstein and Quake III Arena. To put it short, et-sdl-sound is a working ALSA support hack for ET, RTCW and Q3 (and all mods for those binaries).

---

### Post by Azure.Rise on 2008-11-21
Try this:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Put that in the terminal. It'll only affect the current session.

---

### Post by soreau on 2009-10-28
Figured I'd post here since I can't find this solution anywhere else. I am on gentoo and when I ran et after a fresh install I got:

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

I fixed this by changing seta snddevice "/dev/dsp" to this:
```
seta snddevice "/dev/adsp"
```
in the file ~/.etwolf/etmain/profiles/<profile_name>/etconfig.cfg (not to be confused with ~/.etwolf/etmain/etconfig.cfg) after creating a profile <profile_name> in the game. I didn't have to do anything else.

Hope this helps someone, happy fraggin' ;)

---

