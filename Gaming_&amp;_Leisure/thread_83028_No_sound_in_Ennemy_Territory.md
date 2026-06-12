---
title: "No sound in Ennemy Territory"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by tellnes on 2005-10-27
Hey all..
I have just gone from Fedora core 4 to ubuntu, and i love it:p 

Anyway, after installing enemy territory, i dont get any sound the game.
Sound works great in ubuntu in general, music,movies etc..just not in ET:( 

Any idea what plugin, sound system i should use? using esd now, have tried alsa, dident deem to work..

Any tips all you linux gurus out there:)

thx
-tellnes-

---

### Post by seethru on 2005-10-27
is it giving you any errors?

---

### Post by jeffreyvergara.NET on 2005-10-27
try running ET using "sudo et"

---

### Post by tellnes on 2005-10-28
[QUOTE=jeffreyvergara.NET]try running ET using "sudo et"[/QUOTE]

That worked:p 

Noob alert on me!!

So i guess there is something with the permissions then, i installed the game as root, but i changed permissions on the file to allow myself permissions, must be something there anyway. 

Maybe you could explain why this occured, then i could learn something today:)
Thx alot in advance!!

-tellnes-

---

### Post by drummer on 2005-10-28
I put this in the file /etc/init.d/bootmisc.sh (at the end, before ": exit 0") to get sound working in et, without having to run it as root. Putting it in this file just makes sure that it's run when the computer boots, otherwise you'd need to run that command in a terminal as root (not just with sudo) each time you reboot. 
```
#sound for et
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
I've also experienced problems with permissions, especially when et downloads extra .pk3 files, I fixed this by doing this:```
sudo chown -R user:user /usr/local/games/enemy-territory
sudo chown -R user:user ~/.etwolf
```where user is your username. This happened when running et as a normal user, you may not have this problem, but here's my fix if it does happen.

---

### Post by keyes on 2005-10-28
[Ok now it's working fine]

---

### Post by tellnes on 2005-10-30
Well, running et as sudo works, but it just dropps out after a while, also killing esd and running et works, yet i drop out of the game after x amaount of time..so something else must be wrong..i have nvidia drivers and all..just cant figure out why it suddenly stops and trows me back out to the desktop..

---

### Post by tellnes on 2005-11-02
Ok, killing esd, then running ET, it works..for an x amount of time..
I can see in the terminal

reciving signal II
exiting

I get trown out of the game just like that..and suddenly my pc/motherboard started beeping like crazy, like a alarm.

What is this? signal II?

Have to say gaming worked better in fedora:(

---

### Post by easy_target on 2005-11-12
I have been looking for this solution since Warty, and now, here it is! Thank you very much for your effort and help to the gaming community!:D

---

### Post by lateo on 2005-11-12
if u lauch it from pannel, try disable event 'choose menu element' sound:
system>preferences>sound, events, user interface

if from the command line, try exit multimedia apps 5 sec before lanching the game.

---

### Post by PopaKap on 2005-11-15
Hey Im just getting used to ubuntu. ET works but the sound dont. Im running it with sudo and it still dont. This the error im getting if anyone could help me out I would really appreciate it.

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/kelly20/.etwolf/tcetest/ui.mp.i386.so)...
Sys_LoadDll(/home/kelly20/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/kelly20/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No  such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xadcc1cc0
Sys_LoadDll(ui) succeeded!

is it wiritng to the wrong place or should i make it write somewhere else ?
thanks

---

### Post by emperor on 2005-11-15
[quote=PopaKap]Hey Im just getting used to ubuntu. ET works but the sound dont. Im running it with sudo and it still dont. This the error im getting if anyone could help me out I would really appreciate it.

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
[/quote]

looks like it needs the OSS drivers. I found that games need the "sdl" drivers.

libsdl1.2debian-oss  -or- libsdl1.2debian-all

---

### Post by PopaKap on 2005-11-16
sound works in all my other apps  tho

i installed the all one in synapt and box turned green next to it and it still dont work
it is still saying the same error 
thanks for the reply

---

### Post by emperor on 2005-11-16
[quote=PopaKap]sound works in all my other apps  tho

i installed the all one in synapt and box turned green next to it and it still dont work
it is still saying the same error 
thanks for the reply[/quote]

I also have alsa-oss installed and the sound input changed to OSS.

Do you have sound in other linux games like "supertux" or "frozen bubble"?

---

### Post by PopaKap on 2005-11-16
it works in "warsow"
how do i switch it to oss or is that already done ?

---

### Post by emperor on 2005-11-16
[quote=PopaKap]it works in "warsow"
how do i switch it to oss or is that already done ?[/quote]

System - Preferences - Multimedia Systems Selector 

Then change Input to OSS.

---

### Post by windowmaker on 2005-12-16
i have recently install RTCW: ET, and i followed the guide at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) and the sound worked perfectly, however when i turned my PC on this morning the sound for RTCW: ET had stopped working, and i am stumped on how to get it working again =(

---

### Post by ViGiLnT on 2005-12-25
i had no sound in ET before doing what someone said earlier on this thread.
Now ive got sound, but i cant play listening to xmms...only one of the 2 apps must be off in order to the other work...

is there a way to solve this ?

Another question:

is it only me or u guys cant also toggle the console with the "\" button ?

---

### Post by Zimmer on 2005-12-26
[QUOTE=ViGiLnT]i had no sound in ET before doing what someone said earlier on this thread.
Now ive got sound, but i cant play listening to xmms...only one of the 2 apps must be off in order to the other work...

is there a way to solve this ?

Another question:

is it only me or u guys cant also toggle the console with the "\" button ?[/QUOTE]

Hi,
Have a look at my post #6   here:
[http://ubuntuforums.org/showthread.php?t=98167](http://ubuntuforums.org/showthread.php?t=98167)
Works for me... and others..
I now always launch ET from a terminal...
Regards

---

### Post by ViGiLnT on 2005-12-26
I've got sound... Everything that you instructed to do in your post, i have already done...
What I want is to be able to play ET with xmms playing also, i dont know if that's possible...

---

### Post by leetcharmer on 2006-02-04
[QUOTE=emperor]looks like it needs the OSS drivers. I found that games need the "sdl" drivers.

libsdl1.2debian-oss  -or- libsdl1.2debian-all[/QUOTE]

I had the same problem as him
```

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

```
But the libsdl drivers didn't help.

---

### Post by leetcharmer on 2006-02-04
```

sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

```

That worked for me.
It turns out that et wants to get access to all of your sound card, so this should limit it to just what it needs :D

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

### Post by AngryKidJoe on 2006-07-11
```
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
```
How does one undo that? Now ET won't even boot.

---

### Post by Zimmer on 2006-07-11
> **AngryKidJoe said:**
> ```
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
```
How does one undo that? Now ET won't even boot.

It should not be permanent, a re boot would empty the oss file, but hey, go to Nautilus and see if there is any text in the file and if so delete the offending lines...

Personally I do not issue the second of those echo statements to get ET to run with sound..
Are you running ET from a Terminal command?

---

### Post by ubuntu_demon on 2006-07-14
First make sure ubuntu is installed properly:

```
$sudo apt-get install ubuntu-base ubuntu-desktop
```

This will install alsa-oss. oss is needed for sound in a lot of games :

```
$sudo apt-get install alsa-oss
```

You will probably need this module for oss :

```
$sudo modprobe snd_seq_oss
```

If the modprobe didn't give an error make sure it gets loaded with each boot :

```
$ sudo pico /etc/modules
```

and add this line (if it's not there yet) : 
```
snd_seq_oss
```

OSS stuff (mostly games) will still tie up the sound card, but they don't run all the time. Just configure most things to use esound/esd and you'll be good.

Now do a reboot just in case. And before you start :

$sudo su
$echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
$exit 

*I'm not entirely sure whether the second line is needed but it  can't hurt.*

Now start the game :

$cd /usr/local/games/enemy-territory
$./et.x86

Still no sound ? 

You might try to put the word "aoss" in front ($aoss ./et.86) But for me this produces choppy sound while normally my sound is okay.
$aoss ./et.86

You might try killing all esd :
$sudo killall esd
$./et.86

If it still doesn't work try this sound guide :

Comprehensive Sound Problem Solutions Guide
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by Jaymo on 2006-07-23
> **leetcharmer said:**
> ```

sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

```

That worked for me.
It turns out that et wants to get access to all of your sound card, so this should limit it to just what it needs :D

Brilliant, fixed my problem :).

---

### Post by chuck_h1987 on 2007-08-15
the Echo commands worked for me too thanks.

---

### Post by Jedah on 2008-05-28
> **emperor said:**
> looks like it needs the OSS drivers. I found that games need the "sdl" drivers.

libsdl1.2debian-oss  -or- libsdl1.2debian-all

That's how I solved my problem with no sound in ET. It's a common problem with Linux and id Software games. The games seem to work with oss rather than any other driver. Doom 3 required to change the sound system in its cfg file to oss. I highly recommend to install libsdl1.2debian-all instead of changing your system's configuration and creating scripts that kill other sound related processes.

---

