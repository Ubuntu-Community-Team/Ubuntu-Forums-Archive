---
title: "quake 4 libsdl"
date: 2005-10-20
forum: Gaming &amp; Leisure
---

### Post by synrat on 2005-10-20
quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I'm getting this error when trying to run it. amd64, ubuntu 5.4 all SDL libraries are installed. 
ldconfig and LD_LIBRARY_PATH don't have any effect. 

anyone ?

---

### Post by synrat on 2005-10-21
someone pls. help :) !! I don't want to install windows to play quake.
I can paste a strace output if anyone's interested. 

Is everything working ok for Badger users at least ?

---

### Post by Legomancer on 2005-10-21
I'm getting the same error in Breezy Badger.  I made sure the necessary libsdl files were there and even the link is fine.  It seems like Quake is looking for that libsdl file in the wrong place.  I even created a link in the q4base directory just to make sure it wasn't there, but no luck.

I'm going to try a few more things tonight after work and will let you know my results.

---

### Post by synrat on 2005-10-21
I made some progress by installing libSDL in chroot and setting LD_LIBRARY_PATH=/chroot/usr/lib

Now the game starts, graphics and networking works, but no sound. Below's  the alsa error message.  I don't know how to configure this for chrooted env. ( or if that's the problem ) or if there's some kind of command line switch that can set the sound device properly.

I must say, fiddling around with tons of software that won't run on amd64 port is getting old. Too much stuff just doesn't work and there seems to be no end to it.
AMD is really not pushing hard enough on software vendors.  With amounts of AMD CPUS Sun is selling these days you'd expect at least to have a pathetic little java plugin. 

Are you also using 5.10 with amd64 ? and can someone confirm that this actually works without problems on 5.10 x386 ? I'd probably just go with that then. 

dlopen(libasound.so.2)
asoundlib version: 1.0.8
Alsa is available
------ Alsa Sound Initialization -----
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:2672:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Invalid argument
ALSA lib pcm.c:1947:(snd_pcm_open_conf) Invalid type for PCM default definition (id: default, value: cards.pcm.default)
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: Invalid argument
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------

---

### Post by synrat on 2005-10-21
final touch. found this in another post here. 

+set s_driver oss

---

### Post by h4ck on 2005-10-23
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.123.196/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Current search path:
/root/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
TODO: Sys_SetClipboardData
********************
ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.

I Get this eror anyone any idea???

---

### Post by synrat on 2005-10-23
chmod the pak files you copied to 644.

---

### Post by h4ck on 2005-10-24
root@h4ck:/usr/local/games/quake4/q4base # chmod 644 game100.pk4
root@h4ck:/usr/local/games/quake4/q4base # chmod 644 game000.pk4

It is the same eror. IS posible that instalirs is only 19mb big??

---

### Post by synrat on 2005-10-24
did you follow the instructions and copy all pak files from your windows install ??

---

### Post by h4ck on 2005-10-24
i don`t have windows instaler and i dont use windows:D so any other way??

---

