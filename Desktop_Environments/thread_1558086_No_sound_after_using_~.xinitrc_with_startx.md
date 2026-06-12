---
title: "No sound after using ~/.xinitrc with startx"
date: 2010-08-21
forum: Desktop Environments
---

### Post by xcausex on 2010-08-21
I am using a custom minimal install of Ubuntu 10.04 I built up from scratch using mini.iso. All went well till I decided to add .xinitrc to my home dir and autostart.sh (for openbox) to ~/.config/openbox in order to automatically launch a number of common programs when I load up my desktop using startx.

I use alsa for my sound server; I installed alsa-base, alsa-utils and alsa-oss pretty much first thing after installing my new system and sound was working perfectly up until a few hours ago. What gets me is that alsa ought to be loading up as I boot into Linux, I can't see how xinitrc or autostart.sh can even affect it, but it seems switching to using those has caused some sort of issue with it, as I am now without sound.

Everything else worked fine witht he change, my desktop is loading just how I want it now, all the rest of my sorftware is working fine as best I can tell, it's just the sound that is now borked. Has anyone else had this issue, I've searched all over with no luck so far.

If it helps, I am not using any desktop environments, just openbox with a small handful of hand picked packages, I've been running this system for nearly 2 weeks now without any issues until now, and this one has me stumped.

---

### Post by oaliaso on 2010-11-09
having a similar issue. used an alternate install disk in expert mode to install a base system that started out with just xorg and openbox and don't have audio.

using startx with session-openbox in .xinitrc as well.

I have installed alsa-base and a few other related packages...
$alsamixer gives me
cannot open mixer: No such file or directory

Looks like it's looking for a file but I'm not having much luck figuring out which one (still kinda a *nix noobie)

So... BUMP! :)

---

