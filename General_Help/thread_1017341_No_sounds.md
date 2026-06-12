---
title: "No sounds"
date: 2008-12-20
forum: General Help
---

### Post by sudo4re on 2008-12-20
Hello all, new Ubuntu user here and I can't seem to get sound from my machine despite following most of the advices on the forum. I am using a M-audio Revo 7.1 soundcard which works well under Vista and I can hear sounds from my speakers while running Skype in Ubuntu but no mp3's, no sounds from flash apps (youtube etc)... Is there a log or something that I can post to show my problems? I'm sure it's something simple that I have overlooked but for the life of me I can't seem to figure out what it is. TIA.

---

### Post by 2hot6ft2 on 2008-12-21
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
if so try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by balaknair on 2008-12-21
The M-Audio Revolution 7.1 works pretty well on Ubuntu after a few tweaks to get Pulseaudio on track as described here-
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

This is assuming you have Ubuntu 8.10 Intrepid Ibex installed.
You might also want to check this page-
[http://ubuntuforums.org/showthread.php?t=400268&page=9](http://ubuntuforums.org/showthread.php?t=400268&page=9)

---

### Post by kixome on 2008-12-21
If nothing else works, install hardy, 8.04 if you haven't already. Then search synaptic for the word codec, and install any pertinent codecs that you need. also try searching synaptic for flash 10. that way you will have the latest version.

---

### Post by kixome on 2008-12-21
By the way, no matter what anyone says, you should always stick to the LTS (long term support versions of ubuntu) I have found that they always work much better because of solid programming and no experimental stuff. Every time I install 8.10 it messes up ALSA, and various other things.

---

### Post by linux_tech on 2008-12-21
> **sudo4re said:**
> Hello all, new Ubuntu user here and I can't seem to get sound from my machine despite following most of the advices on the forum. 
To get alsa working first install these;
```

sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:
```
gnome-volume-control
```

To open gnome-alsamixer type
```
gnome-alsamixer
```

you will need to go in and adjust settings, unmute and adjust mixers and test.  The settings can vary depending on the machine.

---

### Post by northern lights on 2008-12-21
> **kixome said:**
> By the way, no matter what anyone says, you should always stick to the LTS
This is a personal opinion. Please do not discredit people that you don't agree with. "No matter what anyone says" is not exactly open-minded, eh?

As for the OP's problem:

Can you please post the outputs of ```
aplay -l
```and```
sudo lshw -C multimedia
```Further, check your sound with VLC at best and with sourcefiles that do not require special codecs. A .wav or .ogg at best. Just to eliminate possible causes for error.

Once functional, you may want to run```
sudo apt-get install ubuntu-restricted-extras
```to get support for licensed formats suchs as .mp3

Check [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") for information on how to add DVD and wma/wmv support.

---

### Post by sudo4re on 2008-12-21
Thanks to everyone and their respective inputs. I am able to get the sound working now by following balaknair's advice and tweaked my soundcard per his/her link, much obliged. 

Can I just add this has been a trying and frustrating experience for me but thanks to the helpful advices from this forum, I was able to solve my problem. Thanks again.

---

