---
title: "How to convert ogg to mpg so that it works on Windows"
date: 2007-09-13
forum: Desktop Environments
---

### Post by sigint on 2007-09-13
Use the Synaptic Package Manager to install
gtk-recordMyDesktop 
and
devede

Use gtk-recordMyDesktop to produce the .ogg file and then use devede to do the conversion of the .ogg to .mpg

The .mpg produced works on Windows Media Player in XP (not on Mplayer in Ubuntu).

Rob

---

### Post by DezSP on 2007-09-13
> **sigint said:**
> Use the Synaptic Package Manager to install
gtk-recordMyDesktop 
and
devede

Use gtk-recordMyDesktop to produce the .ogg file and then use devede to do the conversion of the .ogg to .mpg

The .mpg produced works on Windows Media Player in XP (not on Mplayer in Ubuntu).

Rob

.OGGs are playable in Windows, you just need to download the codecs first.

---

### Post by loell on 2007-09-13
you could try 

```
mencoder -idx input_filname.ogg -ovc lavc -oac mp3lame -o output.mpg
```

---

### Post by Spr0k3t on 2007-09-13
If you are trying to convert OGG Theora over to mpeg to upload it to a place like youtube, you can convert the video stream using ff2mpeg... just not sure how to do it off the top of my head.

Edit: loell beat me to it.

---

### Post by JBAlaska on 2007-09-13
Also believe it or not, VLC player ([www.videolan.org/vlc](www.videolan.org/vlc)) can convert your ogg to avi, not the best but for recordmydesktop it works just fine.

---

### Post by sigint on 2007-09-21
Whoops, wrong person!

---

### Post by sigint on 2007-09-21
I tried this first but the mpg's had a strong 3KHz (sampling?) whistle on them + noise.

---

### Post by sigint on 2007-09-21
> **loell said:**
> you could try 

```
mencoder -idx input_filname.ogg -ovc lavc -oac mp3lame -o output.mpg
```

I tried this first but the mpg's had a strong 3KHz (sampling?) whistle on the audio

---

### Post by sigint on 2007-09-21
> **DezSP said:**
> .OGGs are playable in Windows, you just need to download the codecs first.

Thanks, but I can't ask my customers to do that!

---

### Post by frederik.nnaji on 2007-12-03
> **JBAlaska said:**
> Also believe it or not, VLC player ([www.videolan.org/vlc](www.videolan.org/vlc)) can convert your ogg to avi, not the best but for recordmydesktop it works just fine.

Yeah, thanks yo, vlc player works just fine for me, it converted my "istanbul" session that was in ogg video format to h.264 in an asf container. youtube ready my video now.

my task was to convert ogg video ( ogm ) to something youtube can handle

---

