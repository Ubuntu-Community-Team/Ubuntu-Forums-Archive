---
title: "1525n Hardy audio problem"
date: 2009-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gaudentius on 2009-07-22
I did a search on this Dell forum for this specific problem and found nothing.

I've got a 1525N running Ubuntu 8.04.3 LTS running the latest unedited kernal (Linux 2.6.24-24-generic)

I've had audio issues before and searching here has helped.  This is a new issue though.

I recently did an update to what I guess was the audio.  There were a ton on mandatory updates for Pulse Audio and I believe that is what has caused my recent problems.

The touch controls on the laptop will kinda work.  I can push the volume up button and the speaker shows up on screen, but will not do anything. I hit the volume down button and it'll mute ONLY.  I hit the mute button and it'll toggle mute.

***But wait there's more*** . . .

I no longer have a functioning audio jack.  I plug the headphones into the first jack and sound still comes from the internal speakers.  I plug into the second jack and no sound works.

I'm a relative noob and LOVE Ubuntu.  I've had it for almost a year now.  I hope some Ubuntuguru can help.  Thanks.

GD

---

### Post by jerrrys on 2009-07-22
until a Ubuntuguru comes around you may want to try ALSA and OSS.  may get lucky

[ATTACH]122058[/ATTACH]

---

### Post by Gaudentius on 2009-07-23
I noticed that you have HEADPHONE on that list.  I don't.  Any idea how to fix that?

---

### Post by jerrrys on 2009-07-23
may be something to do with dell ubuntu, really don't know.  here's something to ponder

[http://www.google.com/search?q=dell+1525N+headphones+not+working+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=dell+1525N+headphones+not+working+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by brianfactors on 2009-07-23
I had the same kind of problem with volume up/down keys. Except I'm using an Inspiron 1545. 

My other problem was really quite volume.

Umm... I removed pulse with:
```
sudo apt-get autoremove pulseaudio
```

[http://www.linuxtent.com/?p=236](http://www.linuxtent.com/?p=236)

It didn't make the volume higher, but it did fix several other problems. It should help, but it still is a bug. Ubuntu's default sound controller should just work.

---

### Post by jerrrys on 2009-07-23
now that you mention that, there is a headphone switch...[ATTACH]122161[/ATTACH]

---

