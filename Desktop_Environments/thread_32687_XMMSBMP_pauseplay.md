---
title: "XMMS/BMP pause/play"
date: 2005-05-09
forum: Desktop Environments
---

### Post by Gandalf on 2005-05-09
hello,
does anyone of you can pause and then play a song???
because when i press pause and i press after pause or play, the song just begin from the begining it does not resume :(
thanks

---

### Post by kori.mendocino on 2005-05-09
having no problems with bmp, and i dont recall having any with xmms neither. both play and pause keys work fine after pausing.

---

### Post by NeoChaosX on 2005-05-09
What audio output are you using? If you're using the ALSA plugin, you just need to disable MMap mode. Having that enabled causes resuming problems.

---

### Post by JmSchanck on 2005-05-09
I had this problem using alsa. In BMP go to preferences->output->preferences->advanced. and if Mmap is on, turn it off. I dont rlly know what Mmap does (maybe someone else could explain that) but this has worked for me and some other people as well.

Edit:// Whoops someone already answered, sry about that.

---

### Post by Gandalf on 2005-05-11
[QUOTE=NeoChaosX]What audio output are you using? If you're using the ALSA plugin, you just need to disable MMap mode. Having that enabled causes resuming problems.[/QUOTE]
 thanks guys, that works too with XMMS

---

