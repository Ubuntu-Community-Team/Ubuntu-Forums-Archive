---
title: "codec installation..."
date: 2009-02-27
forum: General Help
---

### Post by veda87 on 2009-02-27
whenever i play songs using rythmbox music player...it say MP3 codec is not available.. if i give install, it is not getting installed... 

do you know how to manually download and install........

---

### Post by iaculallad on 2009-02-27
Perform the command below on your terminal:

```
apt-get install 'gstreamer*'
```

---

### Post by blazemore on 2009-02-27
Or better still
```
sudo apt-get install ubuntu-restricted-extras -y
```

Use tab to go to the Accept button... you'll see what I mean.

---

### Post by zvacet on 2009-02-27
Add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your source list.after that in synaptic install w32(or w64 if you use 64 bit version Ubuntu)codecs.

---

### Post by mb_webguy on 2009-02-27
> **zvacet said:**
> Add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your source list.after that in synaptic install w32(or w64 if you use 64 bit version Ubuntu)codecs.

The non-free-codecs package in Medibuntu automatically detects your architecture and installs the correct version of the codecs package.  (This is true for Intrepid, at least.  I don't know about Hardy.)

---

### Post by veda87 on 2009-02-28
now when i imported the MP3 files, it says The GStreamer plugins to decode MP3 files cannot be found....

what should i do now....

---

### Post by gokusupremesayain on 2010-03-25
anytime i try any sudo command the o.s. cant locate the files to install. plz help me

---

### Post by wojox on 2010-03-25
What exactly does it say?

---

