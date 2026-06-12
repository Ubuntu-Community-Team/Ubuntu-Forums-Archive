---
title: "No sound to my 5.1 from my digital opticable?"
date: 2009-02-23
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-23
What do I have to do to get the sound to play to my 5.1 via a digital optical?

It works fine (for the most part) in windows, but doesnt play at all in Ubuntu.

---

### Post by PsychedelicWonders on 2009-02-25
bump

---

### Post by PsychedelicWonders on 2009-02-26
anyone?

---

### Post by PsychedelicWonders on 2009-02-27
bump

---

### Post by PsychedelicWonders on 2009-02-28
bump

---

### Post by jjpcexpert on 2009-02-28
Can one stop bumping!? I have a derivative of Ubuntu called LinuxMint and my 2.1 Stereo Surround works great! Analog is your friend :D

---

### Post by PsychedelicWonders on 2009-02-28
> **jjpcexpert said:**
> Can one stop bumping!? I have a derivative of Ubuntu called LinuxMint and my 2.1 Stereo Surround works great! Analog is your friend :D

Ill stop bumping when I get the answer to my question.

Until then, I'm not going to let my question get lost on page 32.

So I'm trying to do 5.1 not 2.1 and I'm doing digital not analog.

---

### Post by Foxblood on 2009-03-01
Bump

---

### Post by PsychedelicWonders on 2009-03-02
Is a digital optical cable just not that common?

---

### Post by PsychedelicWonders on 2009-03-03
bump

---

### Post by PsychedelicWonders on 2009-03-04
Help

---

### Post by soheil on 2009-03-04
I have problem with my sound blaster 5.1 too. but it seems no one have any idea about it :(

I suggest you to visit this site may be it help you ;)
[http://ubuntulinuxhelp.com/enable-51-surround-sound-on-linux-ubuntu-804-hardy/](http://ubuntulinuxhelp.com/enable-51-surround-sound-on-linux-ubuntu-804-hardy/)

---

### Post by fooman on 2009-03-04
try this:

double click on the speaker/volume icon in the top panel.

when that opens,  make sure that the top option (Device) is set to the alsa mixer.

next,  at the bottom, click on the "preferences" button.

in the box that pops up,  scroll down and put a check next to "IEC958".  ..close that box.

back in the alsa mixer,  click the "switches" tab and put a check next to "IEC958".

see if that works....it did for me back a few kernels,  but somewhere along the way it stopped.  

hope it works for you.

---

### Post by PsychedelicWonders on 2009-03-07
> **fooman said:**
> try this:

double click on the speaker/volume icon in the top panel.

when that opens,  make sure that the top option (Device) is set to the alsa mixer.

next,  at the bottom, click on the "preferences" button.

in the box that pops up,  scroll down and put a check next to "IEC958".  ..close that box.

back in the alsa mixer,  click the "switches" tab and put a check next to "IEC958".

see if that works....it did for me back a few kernels,  but somewhere along the way it stopped.  

hope it works for you.

I dont see a preferences button?

---

### Post by fooman on 2009-03-07
try installing the gnome-alsamixer package. in a terminal:
 
```
 
sudo apt-get install gnome-alsamixer

```after it installs, find it in sound and video...open it and put a check mark next to "IEC958"
 
hope it works for you. :)

---

### Post by dragge on 2009-03-09
That worked for me.. thanks alot!
Only missing that the sound from the analog output stopped when changing.
Lacking the sound in my headset that uses analog.
But my receiver plays the tunes now atleast :D

---

### Post by PsychedelicWonders on 2009-03-28
Took some tweaking, but that seemed to have done it!

Thanks.

---

### Post by sumit.kalra999 on 2009-03-28
Hi,
Similar problem i faced in the begining....
just perfrom hardware test 
```

Administration -> Hardware Testing

```

---

