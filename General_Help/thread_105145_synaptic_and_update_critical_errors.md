---
title: "synaptic and update critical errors"
date: 2005-12-17
forum: General Help
---

### Post by thargs on 2005-12-17
Once again I try linux and am disappointed. I have been away from it for a while and decided to give it a go on a spare machine. Wanted to set it up as a encoder.

Installed Ubuntu 5.10
Installed transcode
Installed ffmpeg

Now I cant run synaptic either via GUI or command. I get a critical error ....null something and it throws me out. I enter password on starting it and then nothig happens.

Update Manager does the same thing. 

The error for synaptic is...

synaptic error 7475 - gtk critical - gtk accel label set accel closure:assertion gtk accel group from accel clsoure (accel closure) ! = null ' failed. 

The error has been 7800.

It repeats itself twice.

So basically I have a broken installation that I cant upgrade or add progs to it. 

Sys specs

1.8 northwood
256 DDR
5900XT
Good mobo

All devices working properly

---

### Post by duminas on 2005-12-18
Try this on a terminal (Programs > Accessories > Terminal):
```
$ sudo aptitude purge synaptic
$ sudo aptitude install synaptic
$ sudo aptitude update
$ sudo aptitude upgrade
```
The first will nuke Synaptic and it's configuration.
The second will install Synaptic again.
The third will have apt check your package list (/etc/apt/sources.list) and update itself if need be. Never hurts to do this.
The fourth will upgrade any packages of which apt (the packaging system both Aptitude and Synaptic are frontends for) is aware.

[size=1]Each dollar sign represents one command. Do not enter or copy the dollar sign when you're inputting a command--it is merely there to show you that each line is its own command.[/size]

---

### Post by thargs on 2005-12-18
Thanks for the reply Duminas.

I fixed it by applying updates to Ubuntu itself. It fixed it but dont know why.

Im sure your solution have fixed it. 

Ta.

---

