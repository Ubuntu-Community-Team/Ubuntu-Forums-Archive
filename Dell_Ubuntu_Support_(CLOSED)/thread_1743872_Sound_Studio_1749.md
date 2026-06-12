---
title: "Sound Studio 1749"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lda4526 on 2011-04-29
Hi All, 
   I would really appreciate any assistance. My computer speakers work fine, but whenever i plug in my headphones they never work, whether its in headphone jack 1 or 2. I have tried many different configurations of editing:

gksudo gedit                            [COLOR=#000000][FONT=courier, monospace][SIZE=2] etc/modprobe.d/alsa-base.conf .

I tried adding [/SIZE][/FONT][/COLOR]                           [COLOR=#000000][FONT=Arial]options snd-hda-intel model=dell-m6-dmic
 
but that did not work.

I have a Dell Studio 1749, i5, 8 gigs of memory, 2 microphone slots. 
I uploaded this to the alsamixer website and would appreciate any assistance. 

[http://www.alsa-project.org/db/?f=a224522061fa63af02608da8479862c54994cfa9](http://www.alsa-project.org/db/?f=a224522061fa63af02608da8479862c54994cfa9)
[/FONT][/COLOR]

---

### Post by mpace965 on 2011-04-30
I have the exact same laptop and the option adding part worked for me. Did you reboot once you made that change?

If you did, check out this post for further help: [http://ubuntuforums.org/showthread.php?t=1459220](http://ubuntuforums.org/showthread.php?t=1459220)

---

### Post by lda4526 on 2011-04-30
Hey thanks for the reply. Once I did the above code, I rebooted and instead of displaying my audio driver/hdmi audio driver, it only displayed one driver that said dummy driver and none of the sound worked. Let me check out that article though.

---

### Post by Novacaptain on 2011-04-30
I have a studio 1747, for me these instructions fixed my headphone jacks:

[http://www.techrecipes.net/operatingsystem/ubuntu/fix-no-sound-headphone-jack-dell-xps-studio-16](http://www.techrecipes.net/operatingsystem/ubuntu/fix-no-sound-headphone-jack-dell-xps-studio-16)

Mine has two headphone slots and one mic slot though. 

To get the microphone to work i had to go to user settings/sound and change the input to "analog input". 

I know that there are a couple of built-in microphones next to the webcam but I haven't bothered with them since i never use them anyway.

---

### Post by lda4526 on 2011-04-30
Hi,
   Last time I tried that, after I rebooted, the only audio configuration that showed up in my sound preferences was "dummy configuration".

---

### Post by lda4526 on 2011-04-30
Hey,
   I just added that line and it resolved my issues this time. Thank you.

---

