---
title: "Mp3 not recognized as audio in nautilus"
date: 2008-03-30
forum: Development CD/DVD Image Testing
---

### Post by Trzone on 2008-03-30
In nautilus, all of my .mp3 files are shown as simple text documents. When i change the file extension to .ogg, .wav or .flac, the icon becomes the familiar music note. Only after i change the file extension, does the music file preview.Here is an attached screenshot to clarify.

I am using Hardy Heron Beta. If any more information is required please be specific. Thanks.

---

### Post by BennBuntu on 2008-03-30
mp3 codecs aren't installed by default, have you installed them? I don't know why they'd show as text files though.

if you haven't, in terminal
```
sudo apt-get install ubuntu-restricted-extras
```

This has a few codecs and things that can't be included by default due to licensing in some countries.

---

