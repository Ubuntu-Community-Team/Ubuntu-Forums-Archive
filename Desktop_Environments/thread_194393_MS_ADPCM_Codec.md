---
title: "MS ADPCM Codec"
date: 2006-06-11
forum: Desktop Environments
---

### Post by jethro10 on 2006-06-11
Hi,
when we convert various avi's from a couple of digital camera we have, they all work except ones the camera encodes with MS ADPCM sound codec.
It plays ok on linux, so it must understand the codec, but ffmpeg and alltoavi only converts the video, givin us a 'silent movie'.
Unfortunatley one mode of the camera I would like to use, forces this audio codec so I have no choice but to use these AVI files.

Any ideas for converting with sound ?

Jeff

---

### Post by nalmeth on 2006-06-11
See what you can do opening the file with audacity (audio editor)

sudo apt-get install audacity

you may be able to do the audio seperately, then use avidemux or something to merge the two. Only an idea, don't know if this helps.

---

### Post by jethro10 on 2006-06-12
[QUOTE=nalmeth]See what you can do opening the file with audacity (audio editor)

sudo apt-get install audacity

you may be able to do the audio seperately, then use avidemux or something to merge the two. Only an idea, don't know if this helps.[/QUOTE]

I'll try that.
It's a bummer.....
J

---

