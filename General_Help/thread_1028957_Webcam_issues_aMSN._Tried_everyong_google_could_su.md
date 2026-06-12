---
title: "Webcam issues aMSN. Tried everyong google could supply."
date: 2009-01-02
forum: General Help
---

### Post by maddog46113 on 2009-01-02
Im having troubles with my webcam in aMSN. It works in Cheese and Ekiga. Ive tried everything i could find in google.....

When i try to send a webcam invitation i get...
>  Your webcam uses a combination of pallettte/resolution that this extension does not support yet 

Heres what i have done so far:

Compiled v4l2 and installed it.
Compiled Easycam2 and installed it.
Compiled Farsight2 and installed it.
Compiled aMSN svn and installed it.
Compiled Flashcam and installed it.

Nothing is working.... 

webcam is a CIF Single Chip. Anyone have a solution that works?

Camorama gives me this output:
```

aaron@Demonic:~$ camorama -D

VIDIOCGCAP
device name = CIF Single Chip     
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 352
max height = 288
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 176
height = 144
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 176
height = 144
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 30069
hue = 0
colour = 0
contrast = 0
whiteness = 0
colour depth = 8

VIDIOCGMBUF
mb.size = 409600
mb.frames = 4
mb.offset = 102400
Unable to capture image (mmap).

```


:confused::confused::confused::confused::confused::confused::confused:

---

