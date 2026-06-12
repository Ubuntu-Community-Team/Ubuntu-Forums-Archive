---
title: "how to convert mp3 to wav ??"
date: 2009-06-15
forum: General Help
---

### Post by abhilashm86 on 2009-06-15
is there tool which converts audio formats in terminal?? i don't want GUI type, is there any??

---

### Post by asmoore82 on 2009-06-15
mpg321 or mplayer or SoX

```
for mp3file in *.mp3
do
   mpg321 "$mp3file" --wav "${mp3file%.mp3}.wav"
done
```:KS

---

### Post by abhilashm86 on 2009-06-16
> **asmoore82 said:**
> mpg321 or mplayer or SoX

```
for mp3file in *.mp3
do
   mpg321 "$mp3file" --wav "${mp3file%.mp3}.wav"
done
```:KS

works great, does this mpg321 support all type of conversions??

---

### Post by sedawk on 2009-06-16
GUI: audacity.

no GUI: sox.

---

### Post by bigboy_pdb on 2009-06-16
I don't know which conversions mpg321 supports, but ffmpeg supports other forms of conversion.

If it doesn't seem to convert certain files, you may need to install some alternate libraries (libavcodec52 and libavcodec-unstripped-51).

I've used this program to convert between video and sound formats.

---

