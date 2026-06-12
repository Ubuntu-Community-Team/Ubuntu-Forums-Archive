---
title: "No Sound"
date: 2005-07-15
forum: Desktop Environments
---

### Post by docnova on 2005-07-15
Hi. I am new to linux and I am having trouble getting my sound working properly. I am running a system with a Biostar M7NCD mother board that uses a Realtek ALC650 6-Channel AC97 sound chip. I am getting a sound effect at the ubuntu login screen but no sound after that. I have tried [this](http://www.ubuntuguide.org/#configuresoundproperly) and it didn't work. Does anyone know what could be causing this?

---

### Post by l.tambiah on 2005-07-15
It may be possible that your channels maybe on mute or turned down. To ensure this open a terminal and type "alsamixer". You will then be presented with alsamixer app. Turn up all the channel and ensure channels are not muted. Then test your sound.

---

### Post by docnova on 2005-07-15
lol no man its more serious that that.... I can here mp3 files now but not system files or audio cd's. anyone else have any ideas?

---

### Post by docnova on 2005-07-16
Anything??? I can get sound for mp3's in XMMS but not cd's. I can get sound in the game tux racer also. I get no system sounds except for the little clip at the login screen.

---

### Post by docnova on 2005-07-16
Alright I fixed it... I had to configure my "/etc/libao.conf" file. I didn't have my defualt driver as alsa.

---

