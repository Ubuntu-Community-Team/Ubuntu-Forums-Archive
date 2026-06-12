---
title: "I can't play avi and other video files"
date: 2009-03-23
forum: General Help
---

### Post by yildiz.a on 2009-03-23
Hi, I am a new user on Linux and I can play audio files but not play video files. I installed all available codecs from Add/Remove Applications, but it didn't work. As I  investigated, playing video files such avi require non-free codecs. Can anyone help?

---

### Post by bertolo on 2009-03-23
try VLC player.
use synaptic pack manager.

---

### Post by Locutus_of_Borg on 2009-03-23
sudo apt-get install ubuntu-restricted-extras

---

### Post by mb_webguy on 2009-03-23
Add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"), then install the libdvdcss2, non-free-codecs, and ubuntu-restricted-extras packages.

---

