---
title: "Another Enemy Territory Thread"
date: 2011-05-14
forum: Gaming &amp; Leisure
---

### Post by 5RR on 2011-05-14
Yeah, no sound problem again. On ubuntu 10.10, but all the terminal things don't work. 

esd: no process found

I've also put my sound all the way up in highest quality. nothing.

help? D:

---

### Post by lisati on 2011-05-14
Have you applied all updates? Which "terminal things" don't work?

---

### Post by 5RR on 2011-05-14
I have. An old thread said,

sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

Is a for-sure fix, but it doesn't work.

---

### Post by Soulcage on 2011-05-15
Method 4 should work: [https://help.ubuntu.com/community/EnemyTerritory#Method%204]("https://help.ubuntu.com/community/EnemyTerritory#Method%204")

---

### Post by betterhands on 2011-05-23
> **Soulcage said:**
> Method 4 should work: [https://help.ubuntu.com/community/EnemyTerritory#Method%204]("https://help.ubuntu.com/community/EnemyTerritory#Method%204")

Method 4 worked for me (thanks!), but use his attached script as opposed to following the original instructions which have you create your own with source from [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz).  server was not found for me.

---

### Post by OakRaider4Life on 2011-06-28
> **betterhands said:**
> Method 4 worked for me (thanks!), but use his attached script as opposed to following the original instructions which have you create your own with source from [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz).  server was not found for me.

The link to this alternate script does not appear to work anymore :(

---

### Post by slaapp on 2011-06-29
> **5RR said:**
> Yeah, no sound problem again. On ubuntu 10.10, but all the terminal things don't work. 

esd: no process found

I've also put my sound all the way up in highest quality. nothing.

help? D:try this worked for me [http://www.prime-squadron.com/modules.php?name=Forums&file=viewtopic&t=3304&postdays=0&postorder=asc&start=0](http://www.prime-squadron.com/modules.php?name=Forums&file=viewtopic&t=3304&postdays=0&postorder=asc&start=0)

---

