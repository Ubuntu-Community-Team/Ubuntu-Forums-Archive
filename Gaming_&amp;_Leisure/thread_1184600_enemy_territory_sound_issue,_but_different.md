---
title: "enemy territory sound issue, but different"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by BlokX on 2009-06-11
SOLVED: I stumbled upon (not actually using StumbleUpon...lol) this link: [http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)

Not sure how I missed it before, but out of all the nonsense I've gone through...2 lines at the command did it.  Go figure. :/
----------------------------------------------------------------------------------------------------
old post below incase someone needs it.  it could help. :)
-----------------------------------------------------------------------------------------------------
Before you just skip this one because it's probably the same as the others...it's not!  lol

I've done all of my research and tried everything everyone has had to offer and I still get nothing out of ET.

So a quick background:  my sound works fine.  I'm using a USB headset as the ONLY sound device.  I had to disable my onboard sound in order to get it to work, but it works great.  I haven't had sound issues with anything...until now.  Also, I'm running Jaunty 64bit.

Here is what I get, as far as sound goes, when I run ET
```
------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/trevor/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/trevor/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/trevor/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xedf59f40  
Sys_LoadDll(ui) succeeded!
```Firstly, I do not have a /dev/dsp.  There is a /dev/dsp1 however.

I've tried
```
sudo apt-get install esound
```and that didn't work.

I've also tried
```
killall esd; et; esd
```and I get back "esd: no process killed", the game starts, and still no sound.

I've also done all of this stuff
```
sudo -i[FONT=monospace]
[/FONT]echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss[FONT=monospace]
[/FONT]echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss[FONT=monospace]
[/FONT]exit
```Here's the deal with this...I don't have a card0 folder in /asound/.  I do have "card1" and "default" (i think default is just a symlink to card1) and I have tried changing them out with "card0" in the above commands with no difference.

So...that's where I'm left standing.  I've tried it ALL so far and have had no difference.  I'm assuming that, at this point, it's just because it's looking for /dev/dsp and I only have /dev/dsp1 but I'm not sure how to make it look elsewhere.

Any help would be appreciated.  I've done all that the communities have mentioned so far with nothing.  I'm willing to try whatever at this point.  I wanna play ET and ET mods badly! :)

thanks!

---

