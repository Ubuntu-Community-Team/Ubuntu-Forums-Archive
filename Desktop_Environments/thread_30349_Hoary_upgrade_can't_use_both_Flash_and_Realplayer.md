---
title: "Hoary upgrade can't use both Flash and Realplayer"
date: 2005-04-28
forum: Desktop Environments
---

### Post by jonti on 2005-04-28
The problem occurs after a fresh install of warty 4.10, brought fully up to date, then upgraded to hoary 5.04 using synaptic. Following the method on ubuntuguide.org I've then installed Nvidia drivers, Java, Flash, and Realplayer 10.

When System-->Preferences-->Sound is set to "enable sound server startup" and the system is restarted then the Flash plugin works just fine in Firefox, but the Realplayer plugin does not. Instead it causes firefox to hang, maybe the whole system(!).  Also, dragging an html file to a browser window to open the file doews not work. What happens instead is that Firefox opens a runaway series of browser windows...

When System-->Preferences-->Sound is NOT set to "enable sound server startup" and the system is restarted then the Realplayer plugin works just fine in Firefox, but the Flash plugin does not.

Stopping ESD does not enable Realplayer, if the system was previously started with System-->Preferences-->Sound set to "enable sound server startup".

I've followed the instructionsin the "Howto: about sound in Hoary & Linux" -- specifically, my /etc/esound/esd.conf is as recommended ...
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

If I type  ...
   lsof /dev/snd/*  
or if I type ...
   lsof /dev/dsp 
nothing is listed in either case.

My system has the dreaded VIA motherboard chipset VIA VT8363A Apollo KT133A, with the VIA AC'97 Audio Controller.

Here is the output of "lsmod|grep snd" ...
snd_via82xx            25248  1
snd_ac97_codec     64608  1 snd_via82xx
snd_pcm_oss          47652  0
snd_mixer_oss        16768  2 snd_pcm_oss
snd_pcm                 84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer               23300   1 snd_pcm
snd_page_alloc       9604    2 snd_via82xx,snd_pcm
gameport               4608    1 snd_via82xx
snd_mpu401_uart   7168     1 snd_via82xx
snd_rawmidi           22944  1 snd_mpu401_uart
snd_seq_device     8332     1 snd_rawmidi
snd                        50276   9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              9824  2 snd

This is a problem for me.  One workaround is just to change the sound server startup setting, logout, and login again.  That method enables me to chose whether to run Realplayer or Flash.  That's kinda clumsy, but it does hint that a more elegant workaround is possible.  Ideally, of course, I could watch and isten to the BBC in my browser (using Realplayer), then surf off to watch and listen to Jibjab or whatever using Flash.

My suspicion is that this is somehow related to nVidia and the X.org changes as I earlier had everything working just fine on this box under Mandrake 10 (Community edition) which uses XFree86. But I don't know.  I'd appreciate any assistance in sorting this out, please.

---

