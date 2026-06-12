---
title: "No Sound in Any Browser"
date: 2010-08-03
forum: Desktop Environments
---

### Post by isoscelesrectangle on 2010-08-03
Sound works on my USB Speakers (I've selected USB_AUDIO in the Multimedia section of the control System Settings). However, when I open a browser like firefox, or chromium, or konqueror, I get no sound when I load a video on Youku or listen to music on Grooveshark. What am I doing wrong?

---

### Post by ankspo71 on 2010-08-03
Hi,
Do you have have one of these two packages installed?
ubuntu-restricted-extras
kubuntu-restricted-extras
I prefer to use both in Kubuntu.
They provide extra packages for codecs (and several other things).
Hope this helps.

---

### Post by isoscelesrectangle on 2010-08-03
Yeah, I have kubuntu-restricted-extras installed. The codecs aren't the problem. I just don't think that firefox is sending the sound to the correct channel. (HDA_INTEL instead of USB_AUDIO).

---

### Post by sosaited on 2010-08-04
Try to install

sudo apt-get install flashplugin-nonfree-extrasound

OR

flashplugin-nonfree-pulse

---

### Post by isoscelesrectangle on 2010-08-04
I don't think any of those exist. 
```
kevin@kevin-desktop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
kevin@kevin-desktop:~$ sudo apt-get install flashplugin-nonfree-pulse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-pulse

```
I do have the restricted repository enabled.

---

### Post by isoscelesrectangle on 2010-08-05
ummm... Bump

---

### Post by isoscelesrectangle on 2010-08-06
ummm... bump 
I really need some help here.

---

### Post by ankspo71 on 2010-08-06
Hi,
Try going into bios and disabling the Intel card. 

Typical instructions to do that:
Reboot. Then during bootup you should see a "Press Del to Enter Bios" message (or something similar), press the key it says to press. When the bios appears, look for "integrated  peripherals" which should be in the advanced settings. You will be looking for something like Onboard Audio, or Intel Audio, etc. Mark it as disabled, then Press F10 to save the settings and exit. 
Hope this helps.

---

### Post by isoscelesrectangle on 2010-08-06
I just turned off the integrated sound in the BIOS, but I still get no sound. Any clues?

---

### Post by isoscelesrectangle on 2010-08-06
umm... Bump?

---

### Post by FallFromGrace on 2010-08-06
Does it work with headphones?

---

### Post by sosaited on 2010-08-19
> **isoscelesrectangle said:**
> I don't think any of those exist. 
```
kevin@kevin-desktop:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
kevin@kevin-desktop:~$ sudo apt-get install flashplugin-nonfree-pulse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-pulse

```
I do have the restricted repository enabled.
They are in Multiverse [ [http://packages.ubuntu.com/lucid/flashplugin-nonfree-extrasound](http://packages.ubuntu.com/lucid/flashplugin-nonfree-extrasound) ]. Check if you have enabled those, and then try again. I had the same problem on Karmic, and installing these packages solved it for me.

---

