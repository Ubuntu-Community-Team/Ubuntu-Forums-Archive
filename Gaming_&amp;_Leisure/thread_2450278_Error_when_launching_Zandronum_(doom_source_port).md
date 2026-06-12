---
title: "Error when launching Zandronum (doom source port)"
date: 2020-09-10
forum: Gaming &amp; Leisure
---

### Post by jcdenton1995 on 2020-09-10
Hello all,

So I've tried to insall Zandronum (a doom source port) for the second time and keep getting the following error when I try to run it...

```
Gtk-Message: 16:17:49.255: Failed to load module "canberra-gtk-module"
Zandronum 3.0.1 - 191013-1938 - SDL version
Compiled on Nov  3 2019
Using video driver x11

M_LoadDefaults: Load system defaults.
Gameinfo scan took 0 ms
W_Init: Init WADfiles.
 adding /usr/games/zandronum/zandronum.pk3, 689 lumps
 adding /home/perrywinklesnoop/.config/zandronum/DOOM.WAD, 2306 lumps
I_Init: Setting up machine state.
CPU Vendor ID: AuthenticAMD
  Name: AMD Ryzen 5 3400G with Radeon Vega Graphics 
  Family 23 (23), Model 24, Stepping 1
  Features: MMX MMX+ SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2
I_InitSound: Initializing FMOD
FMOD Sound System, copyright &#65533; Firelight Technologies Pty, Ltd., 1994-2009.
Loaded FMOD version 4.24.16
OSS could not be initialized. Trying ALSA.
double free or corruption (!prev)
Aborted (core dumped)


```

I wouldn't even know where to start with this, I've searched online for "double free or corruption (!prev)" but only turned up developer forums which are a bit above my pay grade. If anyone can point me in the right direction that would be great!

---

### Post by mastablasta on 2020-09-11
looks like it can not startup the sound. Is sound otherwise working normally? maybe a library is missing

how did you install it? using tarball?:
```
**On Generic Linux based OS**


[LIST=1]
[*]Extract the tarball to the location of your choice.
[*]Install IWADs to ~/.zandronum/ or other location if you modify the ini.
[*]Run the included
[/LIST]

```
or did you add repo?

you can also try Doomsday Engine. it works fine for me. + they made a lovely full screen GUI and you can add 3D files easily if you want to replace the sprites for a more modern feel.

---

### Post by jcdenton1995 on 2020-09-11
> **mastablasta said:**
> how did you install it? using tarball?:


Yes, all sound is working normally.

I added the PPA, there was a slight issue which I *think *I sorted. Basically the command on the Zandronum web page to add the public key is as follows...```
wget -O - http://debian.drdteam.org/drdteam.gpg | sudo apt-key add -
```...basically my interpretation of that is that it makes stdin the destination for the output file, and then the second half of the command uses stdin as the source for the gpg file to add to /etc/trusted.gpg.d/ - this didn't seem to work for me as I got an error telling me that a public key was missing, so I just retrieved the public key with wget and then moved it over to /etc/trusted.gpg.d/ as root, before installing Zandronum.

I'm not sure if there is some issue there, weather perhaps there is a particular library that couldn't be fetched as a result?

Also yes I will give Doomsday Engine a try, I'd like to get Zandronum working too but definitely will see what else there is.

---

### Post by mastablasta on 2020-09-12
try with the tarball. it's been a while since i last installed zandronum. The tarball is binary, so you would just download it, unpack it (&add the wads) and execute it (after allowing to run it).

edit - i tried it with tarball. you actually need to put wads into 

/home/*username*/.config/zandronum/

or change the .ini fle found in there.


so their website instruction is wrong as the zandronum folder is inside config, not in home.

also in my case when switching to full screen it threw the output to TV instead of keeping it on monitor. i am not sure how programs can actually do that since TV is a disabled screen in nvidia and KDE. otherwise it works. i ran it from terminal and the only complaint was that a demo was missing. :) you can record those yourself if you actually need them.

---

### Post by jcdenton1995 on 2020-09-12
Okay, so I downloaded the tarball, which initially didn't want to run because it couldn't see "libSDL-1.2.so.0", which I do have but it's in with my steam installation. I couldn't work out how to point the Zandronum executable to it's location so I just ran...```
sudo apt install libsdl1.2debian
```...which did solve that problem, but now I'm getting the following error in terminal...```
Gtk-Message: 10:21:50.556: Failed to load module "canberra-gtk-module"
Zandronum 3.0 - 170901-1140 - SDL version
Compiled on Sep  1 2017
Using video driver x11

M_LoadDefaults: Load system defaults.
Gameinfo scan took 0 ms
W_Init: Init WADfiles.
 adding /home/perrywinklesnoop/zandronum/zandronum3.0-linux-x86_64/zandronum.pk3, 689 lumps
 adding /home/perrywinklesnoop/.config/zandronum/DOOM.WAD, 2306 lumps
I_Init: Setting up machine state.
CPU Vendor ID: AuthenticAMD
  Name: AMD Ryzen 5 3400G with Radeon Vega Graphics 
  Family 23 (23), Model 24, Stepping 1
  Features: MMX MMX+ SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2
I_InitSound: Initializing FMOD
FMOD Sound System, copyright &#65533; Firelight Technologies Pty, Ltd., 1994-2009.
Loaded FMOD version 4.24.16
OSS could not be initialized. Trying ALSA.


*** Fatal Error ***
Address not mapped to object (signal 11)
Address: 0x7feec08e3548

Generating zandronum-crash-09_12_2020-10_21_50.20798.log and killing process 20798, please wait... 27    ../sysdeps/unix/sysv/linux/wait4.c: No such file or directory.
warning: Memory read failed for corefile section, 4096 bytes at 0xffffffffff600000.
sh: 1: gxmessage: not found
Killed


```
I'm sure I've had this exact error or one very similar before, on my old laptop running Ubuntu 18.04 LTS, which I did eventually get working, however as I remember it, it just miraculously worked one day when I tried it, so that's not much help :D

---

### Post by mastablasta on 2020-09-12
check: ```
zandronum-crash-09_12_2020-10_21_50.20798.log

```
also i didn't add any libraries. it just worked. do you maybe need 32bit libraries installed even if it's 64 bit game?

```
sudo dpkg --add-architecture i386
sudo apt update

```

does that still work in 20.04? i never tried it there... 

btw i tried it on 18.04 Kubuntu  and it is using X not wayland.

Also, i still see the error about sound chip in your output.

---

### Post by jcdenton1995 on 2020-09-15
> **mastablasta said:**
> also i didn't add any libraries. it just worked. do you maybe need 32bit libraries installed even if it's 64 bit game?

I believe I have the 32 bit libraries as I've installed WINE and I'm 99% you have to add them for that, I definitely recognise the command anyway 

> Also, i still see the error about sound chip in your output.

So I found a forum post (can't remember which forum) basically saying it's a known issue that has supposedly been fixed for the release I have (3.0 I believe) but as a workaround the user can start the game with the '-nosound' parameter and change the output system to 'SDL' and then restart the game with sound. Even when I do this a lot of the sound settings won't work, but I can get enough to have some music and all the sound effects. 

So I've got it to run okay, but to be honest the biggest issue is input bugs, the mouse cursor in the menu will randomly disappear, the keyboard will work fine and then suddenly cease to work within menus while still working in game, the gamepad dead-zones will suddenly reset themselves to zero, causing the pad's stick drift to cause a sudden and overwhelming barrage of settings changes while I try in vain to bring the situation under control. It's quite apt really as setting up the game pad is a bit like actually going to hell.

Also for some reason if I press 'T' then the whole program locks up and I can't tab out, open a terminal, switch to another TTY, nothing at all, and I just have to do the REISUB thing (I'm not actually sure technically what this does but I believe it's slightly more graceful than a hard shutdown?). Sometimes this also happens when playing with the video mode settings.

Also if the game crashes but I can switch to another TTY, once I go back to the DE it's all zoomed in and messed up and I have to restart it.

So basically I think it's going to be a work in progress for a while, as I do really like the game, especially with the Brutal Doom mod ;)

---

### Post by mastablasta on 2020-09-16
they also have version 3.1. you could try that if they managed to fix the issues you have.

and doomsday engine? have you tried that? i added 3D models; openGL, added some special effects, weapon models and it's like a completely different game. with all these face lifts, they aged really well. also without them the game still looks good. but i forgot plenty of "secrets". used to play it (Doom 2) a lot...

---

### Post by jcdenton1995 on 2020-09-16
Thanks, I just tried 3.1 briefly, and it does have the same problems, but I've managed to wrestle it into a place where it is playable with the gamepad (I prefer this but also don't have a desk so it's also necessary).

It would actually be easier to configure the key bindings and gamepad axis from the 'zandronum.ini' file, at least then I wouldn't need to wrestle with the buggy user interface, but I'm not sure how to find out what the right syntax would be to put in it. I'm going to join the Zandronum forum and see if anyone there has any specific knowledge on it, and I'll post here if I find anything out.

In terms of Doomsday engine, I'm unsure, I watched some videos of it online and it seems to be closer to old school doom than Zandronum + Brutal Doom, and it's the modern FPS elements of Zandronum plus the great Doom level Design and soundtrack that I am into, although you can correct me if I'm wrong :)

---

