---
title: "Quake4 voices"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by eisle89 on 2006-12-17
I'm using " sudo quake4 +set s_driver oss " and still no voice in game ( tried plain " sudo quake4 " before). music and sound effects work OK. anyone with a fix ?? TIA

---

### Post by Brynster on 2006-12-18
> quake4 +set s_driver oss

needs to be entered as a launch option.

This is done by right clicking on the icon and selecting properties. Then on the 3rd tab on th window that opens should be a launch option box if you paste that instruction there then i *should* cure the sound issues.

( sorry for the vagueness i am in work and no linux here)

---

### Post by eisle89 on 2006-12-18
Thanks for the help Brynster, I tried that already. Is there maybe a quake4.cfg file I'll need to edit maybe ?? I can't find any such file though.

---

### Post by vayde on 2006-12-20
> **eisle89 said:**
> Thanks for the help Brynster, I tried that already. Is there maybe a quake4.cfg file I'll need to edit maybe ?? I can't find any such file though.

It's in ~/.quake4/q4base/Quake4Config.cfg

---

### Post by eisle89 on 2006-12-20
I think I'm narrowing this down. i don't have a Quake4Config.cfg file in the base folder. I do have an arena_ctf.cfg, ctf.cfg, dm.cfg, teamdm.cfg and tourney.cfg. I've played a couple of levels as single player and some online dm's and everything seems fine except the voices. I'm playing on a Shuttle SN25P so I have the nForce4 chipset with the Envy sound, maybe the sound chipset isn't setup correctly. Thank you alot for the time and help

---

### Post by vayde on 2006-12-20
There are 2 directories with the same name.  q4base is in /usr/local/games/quake4 as well as your home directory under .quake4.  The config file is in your home directory.

---

### Post by eisle89 on 2006-12-20
Thanks for the reply. Found it, is there anything I can change there to get the voices working ?? TIA

---

### Post by vayde on 2006-12-21
> **eisle89 said:**
> Thanks for the reply. Found it, is there anything I can change there to get the voices working ?? TIA

I had to change the following:
seta s_driver "default"

to:

seta s_driver "oss"

that did it for me.

---

### Post by eisle89 on 2006-12-21
Damn, that's what mine says now Her's the rest of the sound stuff from the .cfg:

seta s_maxChannelsMixed "24"

seta s_musicVolume "0.5"

seta s_decompressionLimit "2"

seta s_globalFraction "0.8"

seta s_playDefaultSound "1"

seta s_maxSoundsPerShader "0"

seta s_doorDistanceAdd "150"

seta s_volume "0.5"

seta s_radioChatterFraction "0.9"

seta s_speakerFraction "0.65"

seta s_numberOfSpeakers "2"

seta s_subFraction "0.5"

seta s_meterTopTime "2000"

seta s_reverse "0"

seta s_spatializationDecay "2"

seta s_dsp "/dev/dsp"

seta s_driver "oss"

seta s_alsa_lib "libasound.so.2"

seta s_alsa_pcm "default"

Anything look out of place to you ...... TIA

---

### Post by vayde on 2006-12-21
Looks exactly like mine.

I had some problems with a login sound hanging up and locking the sound.  

'ps ax |grep sound' found the problem.  Once I got rid of the sound process that was hanging up and rebooted, all was well.  I don't understand why I needed to reboot, but that did it for me.

---

### Post by eisle89 on 2006-12-28
Here's the output for that on my machine :

eisle89@eisle89-desktop:~$ ps ax |grep sound
 8345 pts/0    S+     0:00 grep sound

What does this tell me ..... I'm a n00b if you haven't figured that out yet ;)

---

### Post by vayde on 2006-12-28
'ps' shows alll running processes.  the 'ax' are options passed to 'ps'.  90% of the time when you use 'ps' you are going to use the 'ax' options.  Why it's not set up that way by default, I don't know.  There's probably a good reason.

'|' is a pipe, that takes the output of the previous command and throws it at the subsequent command.

grep is a pattern matching program.  'grep sound' is telling grep to look for anything containing the string 'sound'.

Put it all together: 'ps ax |grep sound', and you are looking at all your running processes, and filtering the output for anything containing 'sound'.  The only thing you found was the pattern matching program itself, looking for sound.  It can be confusing that in searching for processes you find the process that is doing the searching, but it makes sense.  

Apparently you do not have the sound problem I was having, which is good news, but it isn't helpful in solving your underlying problem.

Sorry I can't be more help.

---

### Post by eisle89 on 2006-12-29
Thank you for your time and some Linux education. I've been doing searches and it seems that plenty ( but not all ) of people are having sound probs of one sort or another, do you think it is chipset related or Linux distro related ? Seems I'm on a quest, with your lesson I'll be better equipped. Thank you

---

### Post by vayde on 2006-12-29
No problem my friend.

I don't know enough to guess at what's causing the problem on your end.  I'm still a hack when it comes to things like this.  I went though a bunch of edits on mine, starting, stopping, reloading, editing, re-editing before I got Doom III to work.  I don't know what I did that finally fixed it.  One time it just started to work.

With Quake IV I just had to change the one line in the file above, and all was well.  Of course now it's crashing at a single point in the game, so I'll have to do some more head banging.  

Ahh, the wonders of Linux.  I'll still take it over the alternative.  At least here I know that eventually I or someone else WILL find the answer.

---

### Post by pm124493 on 2007-01-20
I have followed the recommended fixes to get sound working. From the beginning music and sound effects work fine only voices do not. Looking at the console while running the game and noticing that when someone speaks or there is a computer announcement the file running is an ogg file. Since I can not find any ogg files in the quake4 folders, I am assuming they are in the compressed files.
If I leave the game and run an ogg file I can hear them fine. There seems to be a disconnect in the game running ogg files to the dsp device. I am hoping someone much smarter than I can figure this out. So far this is the only thing not working and it would be a shame to have gaming in Linux suffer for minor glitches.

---

### Post by eisle89 on 2007-02-15
pm124493, do you also run a nVidia sound driver and an AMD64 proc ??

---

### Post by pm124493 on 2007-02-25
eisle89
I have a P4 640 running 6.10 Ubuntu 32bit with an Nvidia 6600GT video card. GNOME Desktop.
Sound device is on an ECS 915P-A motherboard.
CMI9980 ALSA Capture Device
INTEL ALSA Control Device
CMI9880 ALSA Playback Device
CMI9880 OSS Control Device
CMI9880 OSS PCM Device

---

### Post by coffee on 2008-09-20
You need to copy the file named zpak_english.pk4 off of the 1st disc if you have the cd or just off of the dvd otherwise.

I had the same trouble until I realized I missed that one.  Now all the sounds are there.:guitar:

---

