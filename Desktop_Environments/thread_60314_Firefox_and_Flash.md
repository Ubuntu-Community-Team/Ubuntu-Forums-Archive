---
title: "Firefox and Flash"
date: 2005-08-27
forum: Desktop Environments
---

### Post by ZosoPage on 2005-08-27
Forgive me if there is a thread that is already somewhere in here, but the search function is not working at the moment.  
I am a new Linux user, installed on my 11 year olds desktop since he was having problems with Windows XP.  I have mostly everything working, network access, printing to a XP printer, have a firewall installed, but the one thing that I can't get fixed is that firefox will not play audio with flash.  Flash is installed, but no sound.  I do have sound elsewhere, ie GAIM, CD Audio, etc.  Can someone guide me thru what needs to be done to get this to work?  It is a last step to get him working and playing only on the linux box and not on an XP box.

Thank you very much for your time.

---

### Post by Teroedni on 2005-08-27
How did you install flash??
I Installed

---

### Post by Teroedni on 2005-08-27
Have you installed flash from synaptic?
If not try it;)

---

### Post by Teroedni on 2005-08-27
Try to install from Synaptic  :wink:

---

### Post by ZosoPage on 2005-08-27
tried, no change ](*,)

---

### Post by *nix_noob on 2005-08-27
[QUOTE=ZosoPage]tried, no change ](*,)[/QUOTE]
 you mustr restart before the flash plugin will work

---

### Post by *nix_noob on 2005-08-27
you must restart your computer before the plugin will work

---

### Post by Tiede on 2005-08-27
You can always try this also:
```
sudo apt-get install libesd-alsa0
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```
This is to make OSS apps use alsa instead to play sounds... Since Flash uses OSS this might do the trick!

If for some dark and creepy reason it [i]still[/] refuses to work, do this (But be sure to backup the .conf files first to avoid mistakes ;) )

edit your esound.conf 
```
sudo gedit /etc/esound/esd.conf
```
so that is looks like this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
This should kill the Enlightened Sound Daemon (ESD) if it is not needed (sometimes it is the reason some apps won't work.

create the file asound.conf
```
sudo gedit /etc/asound.conf
```
and put this in it:
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}
```
and then restart alsa by doing
```
sudo /etc/init.d/alsa restart
```

enjoy!

---

### Post by ZosoPage on 2005-08-27
[QUOTE=*nix_noob]you must restart your computer before the plugin will work[/QUOTE]


yep, did that, still no sound, have pictures and sound elsewhere, just not in Firefox... site that I use to test is [http://www.comcast.net](http://www.comcast.net) and then click on The Fan...

---

### Post by ZosoPage on 2005-08-27
[QUOTE=Tiede]You can always try this also:
```
sudo apt-get install libesd-alsa0
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```
This is to make OSS apps use alsa instead to play sounds... Since Flash uses OSS this might do the trick!


AWESOME, you made me look good in the eyes of an eleven year old, THANKS... now on to finding something else that I can learn...  \\:D/

---

### Post by c0rderr0y on 2005-08-29
awsome i was looking for a fix like this.

---

