---
title: "Sound in Warcraft 3 and XMMS Music Player"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by scottrick49 on 2007-02-24
First, the good news, which there is alot of.  I have successfully installed ubuntu 6.10 tonight, and gotten warcraft 3 working under wine great.  Very nice so far.  The sound works fine in the game as well.  The problem is that when I adjust the sound in the XMMS music player it also changes the sound in warcraft 3.  How can I fix this?  Thanks!

---

### Post by ViperKnight on 2007-02-24
I'm a bit of a noob at this....

But the problem is XMMS changes your system volume directly instead of within itself.  It's especially annoying with 5.1 (or any system with more than 2 speakers for that matter) since it'll only change the "front" speakers:( 

I just use Amarok while playing games etc.  It uses a different playback engine which has it's own volume control (and not the system volume).  Works great with WC3 ;)

Only thing is the keyboard shortcuts don't work while I'm in WC3.  But I'm sure I can fix that.

---

### Post by Sammi on 2007-02-24
Development of XMMS has stopped. It has been superseded by two newer projects, which have forked and updated it. First [Beep Media Player]("http://en.wikipedia.org/wiki/Beep_Media_Player") and later when development on it also stopped, [Audacious]("http://en.wikipedia.org/wiki/Audacious_Media_Player"), which is active at the moment.

You can install it by adding it's repositories to the sources.list file. You edit sources.list by doing this command in a terminal:
```
gksu gedit /etc/apt/sources.list
```Add two lines based on which version of ubuntu you are using:

Dapper```
deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main
```Edgy:```
deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
```Do these commands in a terminal to install it:
```
sudo apt-get update
sudo apt-get install audacious

```

---

### Post by scottrick49 on 2007-02-24
Thanks, I switched to Amarok and now it is fixed.  

I am having one other problem with sound in warcraft3, though.  The sound works fine when I am in the game, but if I alt-tab out of the game, the sound will have trouble.  Everytime I do something and the game is minimized the sound will stutter for just a second.  Everytime I switch tabs on my browser it stutters.  Not sure if there is anything I can do to fix this.  Anyone else seen this problem and know how to fix it?

EDIT: scratch that; seems like sound is stuttery all the time while I have warcraft3 up and running through wine.  Whenever the song switches on my music player in the background there will be a 1 second stutter, etc, no matter if warcraft is maximized or not.

---

### Post by Sammi on 2007-02-24
I actually use Amarok too :D

Don't know about the stutter though :(

---

### Post by scottrick49 on 2007-02-24
Hmm I have done a bunch more reading, and it seems that the stuttering is being cause by an underrun error:

DSOUND_MixOne underrun on sound buffer 0x18afb0

and also due to the fact that the direct sound emulation in Wine doesn't recieve a high enough thread priority.  This causes the sound buffer to become 'empty' at times, which causes stuttering.  I haven't found a solution to it.  Maybe somebody else has found something?

---

### Post by scottrick49 on 2007-02-25
thought i'd bump this up once today

---

### Post by vinboy on 2007-02-26
how do you guys get use Wine and Amarok at the same time?

Do u guys run Wine with OSS?

---

### Post by Sammi on 2007-02-26
> **vinboy said:**
> how do you guys get use Wine and Amarok at the same time?

Do u guys run Wine with OSS?
This might help you: [https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49](https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49)

---

