---
title: "How to record the sound when calling with skype?"
date: 2008-12-27
forum: General Help
---

### Post by frenchn00b on 2008-12-27
So the sound is already busy for arecord eg:
```
arecord --device=hw:1,0
```

I wanna record all my sound with usb 
```
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

---

### Post by mojoman on 2008-12-28
Perhaps you can use a [_tpipe_]("http://linux.die.net/man/1/tpipe") too redirect the output to both speaker and file?

Haven't tried anything like it myself but I don't see why it shouldn't work. 

/mojoman

---

### Post by frenchn00b on 2008-12-28
```
arecord 
```
alone works and can be 'piped'

```
$ arecord
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 8000 Hz, Mono
RIFF$&#65533;WAVEfmt @data&#65533;~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```


then on that usb mic:


```
$ arecord --device=hw:1,0
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 8000 Hz, Mono
arecord: set_params:904: Sample format non available
 

```

well : you see :( Nothing



**So?**

---

