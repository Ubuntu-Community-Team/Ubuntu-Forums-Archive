---
title: "Sound Issues with ALSA/Intel/Stupidity"
date: 2009-05-14
forum: General Help
---

### Post by chriswinsatlife on 2009-05-14
I was trying to fix a sound error in recording, and ended up installing some random ALSA driver that I shouldn't have (alsa-driver-1.0.14). Now I have no sound.


ls /proc/asound/ returns: "no such directory."

aplay - returns:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: audio open error: No such file or directory

Is there a way I can roll back to the driver setup I had yesterday? Or otherwise fix this mess? Sound worked right out of the box on Jaunty, despite my having the tricky Intel sound card.

Thanks for the help!

---

### Post by Locutus_of_Borg on 2009-05-14
run 'sudo alsaconf'

---

### Post by chriswinsatlife on 2009-05-14
No luck.

"chris@chris-laptop:~$ sudo alsaconf
sudo: alsaconf: command not found
chris@chris-laptop:~$ sudo apt-get install alsaconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsaconf"

---

### Post by Locutus_of_Borg on 2009-05-14
try then:

sudo -i
alsaconf

---

### Post by chriswinsatlife on 2009-05-14
Not finding alsaconf made me double check the re-installation of the newest ALSA drivers. It turned out that alsa-utils did not install correctly, as it fixed my sound problem once I purged/reinstalled that package. 

Thanks for the help!

Funny that I still get "command not found" when I try "sudo alsaconf" from the terminal, but the sound works now either way.

---

### Post by alelondon on 2009-05-15
alsaconf is not part of ubuntu anymore. since version 6. i think...

---

### Post by Ansraliant on 2009-05-15
Why don't you try to install the latest ALSA drivers. It worked for me when jaunty didn't recognize my sound card.

[http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")

I have at home another solution that right now I do not remember. If downloading, removing old drivers, and installing the new ones do not work. Just tell me and I'll post it.

Good Luck!

---

