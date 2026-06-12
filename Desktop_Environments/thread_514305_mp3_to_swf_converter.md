---
title: "mp3 to swf converter"
date: 2007-07-31
forum: Desktop Environments
---

### Post by Eminem on 2007-07-31
Is there any app that can help me convert MP3's to SWF's?

---

### Post by Immolatus on 2007-07-31
try audacity it supports a lot of formats out of the box.

---

### Post by sr20ve on 2007-07-31
I don't know if that is even possible, they are two completely different types of file formats.

You could make an swf with an embedded mp3.

---

### Post by Eminem on 2007-08-01
> **sr20ve said:**
> I don't know if that is even possible, they are two completely different types of file formats.

You could make an swf with an embedded mp3.

It's possible. I've done it in Windows.

---

### Post by avik on 2007-08-01
> **Eminem said:**
> It's possible. I've done it in Windows.

What did you use to do that?

---

### Post by Eminem on 2007-08-02
> **avik said:**
> What did you use to do that?

Total Video Converter.

---

### Post by happysmileman on 2007-08-02
Try TVC in wine then first, though I doubt you'll have much luck

---

### Post by unc0nn3ct3d on 2008-05-30
Late reply but it'll help someone eventually I imagine..

Only way I found to do this was to use ffmpeg to convert it into a .wav first and then wav2swf (swftools) to convert it over to an swf.

FFMPEG: [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)
$svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

swftools: [http://www.swftools.org/](http://www.swftools.org/)
wav2swf doc: [http://www.swftools.org/wav2swf.html](http://www.swftools.org/wav2swf.html)

Done as dinner

---

