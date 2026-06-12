---
title: "performous static sound"
date: 2014-05-02
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2014-05-02
So I love to sing but never have the chance so I downloaded Performous from the repository and I can hear sound like music barely in the back ground, but static sound is so loud. My computer specs are:

HP DC 5750
AMD Athlon 64 x2
8 gig ram
ATI Radeon HD 7750
Lubuntu 14.04

I have tried Frets on Fire but that is not what I am looking for, I would love Ultrastar but there are dependencies that cannot be resolved. I tried pykaraoke but it is not what I am looking for either. I would be looking for something like Performous or Ultrastar, I need something to tune my vocals where I can see my pitch. And of course can use it with karaoke songs would be preferred.

I have tried everything in the  audio settings of Performous and the Loud static sound is persistent on all settings. I tried unplugging the microphone in case it was feedback from the speaker or fan on my computer but it is still there.

---

### Post by vanquishedangel on 2014-05-02
When I start performous in terminal I get this

Performous 0.7.0
  Internationalization:   Enabled
  MIDI I/O:               Disabled
  Webcam support:         Disabled

ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

Then after playing with some settings it shows this added to the above:

Saved configuration to "/home/shawn/.config/performous/config.xml"
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Segmentation fault (core dumped)

---

### Post by jan-c-dittrich on 2014-05-18
Same problem here; I was unable to fix it, too.

---

### Post by Valezan on 2014-06-26
Hi,
 I also have this problem since the upgrade to Ubuntu 14.04. Still no answer?
 Regards

---

### Post by markcgriffiths2 on 2014-07-13
Did anyone fix this?  I have the same problem too.

---

### Post by Valezan on 2014-10-30
Solved for me with Ubuntu 14.10 and Performous 0.8...

---

### Post by dscarlat on 2014-11-06
Hi, Where did you get performous 0.8? Ican only find 0.7...

I've seen the same static noise in Ultrastar Deluxe when the songs are in .ogg instead .mp3...

Regards.

---

### Post by Valezan on 2014-11-07
Hi dscarlat,
I did not do anything, the 0.8 version come with the update of Ubuntu 14.10.
Now, this is the version that I can find in Synaptic. But for another computer which is on Ubuntu 14.04, I don't have the 0.8 version yet. Sorry if I can't help you more.

---

### Post by dscarlat on 2014-11-11
I'm in 14.04 and only 0.7 is available... but no repository found wit 0.8. Thanks anyway!!

---

### Post by oldrocker99 on 2014-11-11
Performus' own website has no later than 0.7...

---

### Post by Valezan on 2014-11-12
Well, I made a mistake because on the game, it is written “Performous 0.8”
[[IMG]http://pix.toile-libre.org/upload/img/1415812626.png[/IMG]]("http://pix.toile-libre.org/?img=1415812626.png")
But effectively, on Synaptic the version is “0.7.0+git201410715-1ubuntu2”
[[IMG]http://pix.toile-libre.org/upload/img/1415812703.png[/IMG]]("http://pix.toile-libre.org/?img=1415812703.png")
Sorry for this mistake.

---

### Post by dscarlat on 2014-11-12
OK. So 0.7 can work without noise.... I'm convinced our problem has to do with .ogg sound... But no idea what to check... Other programs plays ogg fine... But both ultrastar and perfirmous make noise....

---

