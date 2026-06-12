---
title: "Dell Vostro 220 sound fix"
date: 2008-12-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by williemach on 2008-12-21
I just purchased a Dell Vostro 220 and loaded Intrepid Ibex on it. It didn't have sound after installation. I made too many changes before isolating what really fixed my sound, but here's the steps I took:

1. Removed pulseaudo and it's instances from synaptics.

2. Installed the latest Alsa drivers and built from source, using this link - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). I only bothered with installing alsa-drivers, alsa-lib, and alsa-utilities and skipped the rest.

3. After rebooting, I still had no sound. 

4. Out of frustration, I went back to the Ubuntu forums and thought maybe the drivers weren't being loaded. I added this line to the following file (when I mean file, I mean /etc/modprobe.d/alsa-base):

```
~$ cat /etc/modprobe.d/alsa-base | grep model
options snd-hda-intel model=3stack-6ch-dig
```

5. I rebooted again since i'm still new to linux, although i'm sure you could modprobe and get it to work. After reboot, success... sound! 

Here's what I got loaded on my Vostro 220 for a soundcard:

```
desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1
```


Hope this helps someone.



Ok, editing this post since it seems the latest Ubuntu updates have broken sound again. 

First off, the problem isn't the Vostro 220. It's the integrated soundcard it uses. Theres a bug for it, I believe. 

Vostro 220 uses the following hardware:  

Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


I haven't changed anything from my previous steps. To recap, Pulseaudio is completely removed from Synaptics. I have reason to suspect the newest linux headers that Ubuntu is updating with could conflict with Alsa. 

Here's the step-by-step on how to fix the sound (or at least what I did to fix it):

1. Remove all instances of Alsa sound from synaptics.
2. Download and install the Alsa driver, utils, and lib outlined here, [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
3. Once the Alsa driver has been installed, latest was 1.0.19 which release 1-06-09, reboot the computer. 
4. In the sound applet, open the volume control and bring the "Front" playback switch to the highest or whatever setting you prefer.
5. Toggle the master sound and you should now have sound.

---

### Post by ryanlutz on 2009-02-14
Thanks for your post!

I was able to resolve my problems with my newly purchased Vostro 220s. For the record, though, all I needed to do was follow this thread: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810). I believe this breaks and needs to be redone if you upgrade your kernel.

Also, I did not have to uninstall PulseAudio. I have both PulseAudio and ALSA installed and sound is working.

---

### Post by uttern S64 on 2009-02-23
Hello
I tried to follow your instructions but I run into problems when I try to install alsa.
/Magnus

---

### Post by williemach on 2009-03-02
What part of the ALSA install is failing? We can't help you if you don't put in details.

---

### Post by erickpo86 on 2009-04-13
in my vostro 220s don't work!
But i change the version of alsa-lib and alsa-utils to all steps work.
I do only steps 1 to 3 and the sound works!

alsa-driver = 1.0.19
alsa-lib = 1.0.14
alsa-utils = 1.0.14

---

