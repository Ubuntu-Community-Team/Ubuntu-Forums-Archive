---
title: "Inspiron E1505, Ubuntu 9.04 - Noisy/Creaking Sound"
date: 2009-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lshlyapnikov on 2009-04-25
Dell Inspiron E1505.

Upgraded to Ubuntu 9.04 using ubuntu-9.04-alternate-i386.iso.

Something happened with the sound. When I listen mp3, wav or any other files I hear only creaking sound, like I am listening to not tuned radio channel.

Do I have to install any module that supports my built-in audio card?

Thank you,
Leonid Shlyapnikov

---

### Post by Paul S on 2009-04-25
Jaunty has 3 different sound drivers on my card.  One of them causes the same problem you describe.  I'm using kubuntu, and it's changeable under system settings > general tab > multimedia.  Just try them till you find the best.  On mine Analog works best.

hth

---

### Post by lshlyapnikov on 2009-04-25
> **Paul S said:**
>  it's changeable under system settings > general tab > multimedia.  Just try them till you find the best.  On mine Analog works best.

Thanks for the information. I am using Ubuntu. Any idea where it is in gnome?

aplay gives the following output:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Is STAC92xx right driver for Inspiron E1505?

Thank you,
Leonid

---

### Post by hasimir44 on 2009-05-02
Has anyone resolved this? None of the available devices are working correctly - 2 of them have a lot of static and the others have no sound at all. 

static:

  pcsp (Alsa mixer)
  Playback: pcsp - pcsp (PulseAudio Mixer)


Thanks!

---

### Post by sueornot on 2010-04-10
I found this on another reply

"The fuzziness is because your ALSA PCM volume is turned all the way down, so run `alsamixer` in a terminal and turn the PCM volume up. After this is all done, make sure every applications (totem, firefox etc.) is set up to use pulseaudio or alsa as the sound manager."

---

### Post by person9 on 2011-01-12
Solution above worked for me. ^^^^^

Why would this just randomly happen? I have had this problem a few times before with many months in between, so I always forget that it is the issue. Thanks again :o
So glad it is a simple and functional fix.

---

