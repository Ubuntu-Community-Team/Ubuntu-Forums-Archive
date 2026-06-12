---
title: "regnum online crashing"
date: 2012-09-20
forum: Gaming &amp; Leisure
---

### Post by naknak987 on 2012-09-20
ubuntu 12.04 
1 gig dual core processor 
3 gig ram
intel graphics, I dont know anything else about the graphics card. :mad:

when I run the laucher for regnum im a terminal it seems to run fine until I try to enter the world, witch is when it crashes. Heres the terminal output.

```

naknak987@naknak987-KJ297AA-ABA-a6412p:~$ '/home/naknak987/regnum/rolauncher' 
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Segmentation fault (core dumped)
naknak987@naknak987-KJ297AA-ABA-a6412p:~$ Found 1 messages leaked

```

any help is greatly apriciated

---

### Post by lnxnut on 2012-09-26
Just a guess. But as I read the bluetooth on that, I have bluetooth headphones of my own and it crashed regnum.  Had to do away with my bluetooth and direct sound to speakers. Hopefully this will help you.

---

### Post by naknak987 on 2012-10-01
Ok, I dont use bluetooth anything. Not sure why its trying to use bluetooth for. Ill try playing with some setting to see if I can get it to stop using bluetooth. As far as the direct sound to speakers, I have no idea were to start with that.

---

