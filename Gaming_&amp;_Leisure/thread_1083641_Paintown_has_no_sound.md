---
title: "Paintown has no sound"
date: 2009-03-01
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-03-01
Hi.
I have got the game, Paintown. There is no sound from it though? Any solutions?

I installed it with these files:
paintown_3.0-0~getdeb1_i386.deb
paintown-data_3.0-0~getdeb1_all.deb

:confused:

---

### Post by kazzmir on 2009-03-07
Hi, this is the author of paintown. Do other games have sound? Sometimes I have to restart alsa to get sound to work.

sudo /sbin/alsa force-reload

---

### Post by Rytron on 2009-03-08
> **kazzmir said:**
> Hi, this is the author of paintown. Do other games have sound? Sometimes I have to restart alsa to get sound to work.

sudo /sbin/alsa force-reload

Excellent kazzmir. Thank you. That line of code did the job. Sound works fine now.
:popcorn:

P.S There was no problem with sound on other games.

---

### Post by mwillams73 on 2009-04-15
Well I havnt played paintown, but this worked for me also, unfortunately while it solves my gaming sound issues it creates a new one. Now if I want my desktop sounds back I have to reboot, Is there a more permanent fix for this? Or will i have to reboot everytime i want to hear sounds when not playing games. I might as well reinstall xp and just boot into that if have to reboot anyways.

---

### Post by mwillams73 on 2009-04-16
I figured out that if you go into the sound preference, I.E. system/sound/and clik on the sounds tab, then uncheck play system sounds, the games work just fine and then when youre done just recheck play system sounds and it goes back the way it should! 

NOTE: I find its much easier to right clik on the sound preference in the menu and choose add this launcher to panel , that way its always right out where you can easily get to it!
I hope this helps anyone with these problems. 

Thanks for the help!! If you hadnt posted how to reload it i woulda never figured out that unchecking the box was essentially the same but without system wide side effects!!

---

### Post by R33D3M33R on 2009-04-16
Or just do

```
killall artsd
```

or 

```
killall esd
```

---

### Post by crjackson on 2009-12-06
> **kazzmir said:**
> Hi, this is the author of paintown. Do other games have sound? Sometimes I have to restart alsa to get sound to work.

sudo /sbin/alsa force-reload

Sadly that didn't work for me.  Any other ideas?

---

### Post by arkaitzswagman on 2010-08-12
Hello all,

Thanks Kazmiir, it's a really nice looking game. It works great by me except for the sound though.
My OS is Ubuntu Netbook Edition, running the pulseaudio sound server.
I tried to kill all instances running it in the console before  starting the game, but it didn't work either.
Thanks for any help

---

