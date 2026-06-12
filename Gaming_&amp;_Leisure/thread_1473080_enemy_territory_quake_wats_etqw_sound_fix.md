---
title: "enemy territory quake wats etqw sound fix"
date: 2010-05-04
forum: Gaming &amp; Leisure
---

### Post by Cresho on 2010-05-04
Hello!  this works for lucid lynx ubuntu

I'll post my findings here but I would like to know who has a really good fix for pulseaudio and this game.  If I leave it alone, i get a 1 minute delay in audio streight from install of the operating system.

Ill post a quicky

gedit ~/.pulse/client.conf
and add "Adding autospawn = no" without quotes

then

system->preferences->startup applications add
pulseaudio launcher
pulseaudio

then the script for the game

```

#!/bin/bash
killall compiz
killall -9 pulseaudio
cd ~/Installed_Programs/Games/etqw
./etqw
compiz
pulseaudio
```
reboot
just wondering what everybody else is doing here.  I also have mic fix commands but i wont add those.

---

### Post by Cresho on 2010-05-04
here is an update.  stopped working...LOL

any fixes yet?  I read alot so far but I would like to see one that actually works fine.

---

### Post by Cresho on 2010-05-05
found a solution

#gedit ~/.pulse/client.conf
and add "Adding autospawn = no" without quotes

then

system->preferences->startup applications add
pulseaudio killer
pulseaudio -k



reboot to take effect.
works perfect.

create a alsamixer launcher.  use alsamixer to fix your audio issues.  pulseaudio is dead so no need to ressurect it.

right click on the start and edit menu and create a launcher and add

gnome-terminal -e "alsamixer -g"

now you have a terminal that pops up and you can adjust all your volumes and works perfect.

wine now works, windows games works, all etqw works, no problems.  no need to uninstall or modify crap and if you need pulseaudio for what evilness intent you have, just remove the startup exectution and delete the file that you created in the .pulse directory and reboot.  then your good to go without modifying anything

when pulse is dead, it goes back to alsa.  alot of things start to work..

I'll give pulseaudio a benefit of a doubt, it works better than past versions but its still buggy.

---

### Post by fezzle on 2010-05-05
I was getting delayed audio by about 30sec and the frame-rate dropped every few seconds.

this fixed the audio:
apt-get remove pulseaudio 

this fixed the video:
killall compiz


I had to change the output device in audacious from pulseaudio to alsa.  There may be other places where this is required.

---

### Post by Cresho on 2010-05-06
After I did the second solution I posted, etqw ran slow most likely due to lingering pulse audio.  I switched over to kubuntu for the moment.  I was running beta with no problems and I came home to gnome thinking pulse was working.  In fact pulse even kills all my wine games.

I switched to kubuntu running compiz and no problems...sad to say.

---

### Post by mawhrin on 2010-06-05
I used [this script]("http://nullkey.ath.cx/~stuff/et-sdl-sound/") edited (binary is etqw.x86, game dir is etqw) and in autoexec.cfg added "seta s_driver oss"

Works now.

Previously I had a 25-40 second audio lag.

---

### Post by J.K.Makowka on 2010-06-17
> **mawhrin said:**
> I used [this script]("http://nullkey.ath.cx/~stuff/et-sdl-sound/") edited (binary is etqw.x86, game dir is etqw) and in autoexec.cfg added "seta s_driver oss"

Works now.

Previously I had a 25-40 second audio lag.

Doesn't work here (qw doesn't start with this script for ET; yes after modification).

Really crappy bug :(

Strangely all other games work fine, without the sound lag.

I would like to avoid messing with the base system and uninstall pulseaudio...

---

### Post by david_run on 2010-06-21
I have a solution but it creates new pb. Here it is :
In sound preferences by default in "material" I got "Analog stereo duplex" selected.
All sound works well (video, songs, youtube...) exept ETQW.

But if I choose "Digital stereo duplux (iec958 )" No sound works, exept ETQW !!!

It should help some of you and maybe someone could propose a script ?
D.

---

### Post by J.K.Makowka on 2010-09-01
From here:
[http://ubuntuforums.org/showthread.php?t=1564210](http://ubuntuforums.org/showthread.php?t=1564210)

Seems to work for ET:QW also

----------------------------------------------
add this to last line in doom3


+set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"

so that it look like this:


#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/alex/Apps/Games/Doom3/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
-----------------------------------------------------------------------

---

