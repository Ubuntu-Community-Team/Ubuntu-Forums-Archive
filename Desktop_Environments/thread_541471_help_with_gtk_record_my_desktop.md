---
title: "help with gtk record my desktop"
date: 2007-09-02
forum: Desktop Environments
---

### Post by hhpeter on 2007-09-02
Hi 
I installed this software and it records the image but I can't make it record the sound lets say from a streaming video 
When I go in advanced>sound i have this options 
Channels 2
Frequency 22050
Device hw:0,0
Any advice? Thanks

---

### Post by hhpeter on 2007-09-03
now it records the sound from the microphone how do I make it record only the sound from the streaming video?

---

### Post by hhpeter on 2007-09-19
please anybody .....
what should I put in the device section?to record the sound from the media player not from the mic?

---

### Post by loell on 2007-09-19
you will have to configure your alsa mixer , to record from the sound coming from your speaker/sound box

you can install and run **gnome-alsamixer** , then check the check box **"mix"**

---

### Post by hhpeter on 2007-09-19
I installed the gnome-alsamixer when I type in terminal I get this

xxxx@xxxxr-desktop:~$ gnome-alsamixer

** (gnome-alsamixer:16942): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:16942): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:16942): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

and in gnome -alsamixer I don't find any "mix" box I have the following:
Headphone(checked)
IEC958(checked)
Input source(unchecked)
Input source(unchecked)
Input source(unchecked)

Please help....

---

### Post by loell on 2007-09-19
the mixer is also dependent from the sound cards capability, usually it has that mix check box,

can you post your gnome-alsamixer screen shot? just to see the options offered?

---

### Post by hhpeter on 2007-09-19
> **loell said:**
> the mixer is also dependent from the sound cards capability, usually it has that mix check box,

can you post your gnome-alsamixer screen shot? just to see the options offered?

here you go:

---

### Post by loell on 2007-09-20
we'll just be wild guessing here, if you don't mind ;)

can you check those input source check boxes? and those **rec** check boxes then

try recordmydesktop again.

 its good that we have the screenshot of the default setting, so that you can restore it, if ever the mixer becomes messy :)

---

### Post by hhpeter on 2007-09-20
Thanks loell for all your answers, I tried everything I just can't get it to work ..... can you please tell me some others programs that capture the desktop and sound so I can try them ....

---

### Post by loell on 2007-09-20
you can also try xvidcap.

---

### Post by hhpeter on 2007-09-20
> **loell said:**
> you can also try xvidcap.

its the same it records the sound from mic and not from the player...i don't know what to do here is a screen shot of the xvidcap prefferences ...
what shoald I put in input device to record the sound from the player?

---

