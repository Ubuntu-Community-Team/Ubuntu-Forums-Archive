---
title: "Studio XPS 16 Audio problem"
date: 2011-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rjs0015 on 2011-02-02
Hey guys, I've been using Ubuntu since August 2010 (currently on 10.10) but this is the first major problem that I can't seem to find an answer to.

I can't record audio from my computer, but it recognizes the webcam in Cheese (but it is very bad quality).
Under System>Prefs>Sound>Input no input devices even appear.
I tried a something that seemed to work for others which was to edit the alsa-base.conf inside etc/modprobe.d and I also tried creating a file called dellstudio.conf with the same information, which was to add options snd-hda-intel model=dell-m6 to the text.

I have no problems with audio output, just input.
Any ideas?
Thanks in advance.

---

