---
title: "Not getting Quake III Arena working"
date: 2005-07-08
forum: Gaming &amp; Leisure
---

### Post by Gardar on 2005-07-08
Hi... 

Im very new to ubuntu I and I think it's one of the nicest distros I've tryed :)
one problem tho, I am a gamer and I would love to get unreal tournament 2004 and Quake III  working. here are my problems

Quake III Arena
I've done everything they say in the Linuxgamers howto and I type 
```
quake3
```
and all I get is a blank screen but if I move my mouse I see my desktop in like 5x it's size.. and I have to turn off the console I started the game in so I'll get it normal again.
The console stops at Sound initialation 

I hope someone can help me with this

With thanks in advance 

Gardar

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=Gardar]Hi... 

Im very new to ubuntu I and I think it's one of the nicest distros I've tryed :)
one problem tho, I am a gamer and I would love to get unreal tournament 2004 and Quake III  working. here are my problems

Quake III Arena
I've done everything they say in the Linuxgamers howto and I type 
```
quake3
```
and all I get is a blank screen but if I move my mouse I see my desktop in like 5x it's size.. and I have to turn off the console I started the game in so I'll get it normal again.
The console stops at Sound initialation 

I hope someone can help me with this

With thanks in advance 

Gardar[/QUOTE]
 probably a sound or video issue

go to :
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

follow the sound section :
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

also install alsa-oss
$sudo apt-get install alsa-oss

If you got an nvidia also go here :
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

also check these threads out :
[http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)
[http://ubuntuforums.org/showthread.php?t=42492](http://ubuntuforums.org/showthread.php?t=42492)

---

### Post by Gardar on 2005-07-08
I've got the nvidia driver installed and the sound works properly in the system I have alsamixer working and everything

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=Gardar]I've got the nvidia driver installed and the sound works properly in the system I have alsamixer working and everything[/QUOTE]
 then try the other threads I suggested and search the forums :)

---

### Post by raw_hide on 2005-08-08
Hey Gardar,I know this is a little late but I had the same problem and solved it by going to a root terminal and typing "killall esd" (without quotes) and all is well :) 

Good luck...

---

