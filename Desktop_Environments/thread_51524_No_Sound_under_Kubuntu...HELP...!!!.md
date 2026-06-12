---
title: "No Sound under Kubuntu...HELP...!!!"
date: 2005-07-24
forum: Desktop Environments
---

### Post by miguipda on 2005-07-24
Hi,

I previously tried the ubuntu, gnome environment and kde-desktop installation.
All worked perfectly. :razz: 

Today I decided to install the Kubuntu (from the downloadable cd).  To install properly and reduce the system occupation on the hdd.
The installation of the kubuntu was perfect. But now I have a problem. I don't have sound.  #-o 

When I was under ubuntu I had sound then please help me. I use skype (phone VoIP) to talk with many peoples in the worlds and I am now stopped in my job.  :cry: 

Since this morning 9 hr (now it is 16h15) I tried to find a solution. I read a lot of forum (ubuntu and others).
Nothing works.  ](*,) 

Then sorry for the long explanation but I think it may help you to understand and find a solution for me. Sincerely thanks for your help and the time you given to me.

The problem seems to come from the fact that no sound card are seen by the kubuntu installation.

What can I do?

Miguipda ;-)

*****************************************************************************

My computer is a Compaq Deskpro EN Series SFF (600 MhZ with 256 Mb 40 Gb)
Sound card which worked previously under ubuntu is ESS1869 under IRQ5 port 220h

I tried modification on files and even recompilation of alsa driver (1.0.8) with the es18xx driver as shown here below. But nothing changed.


*****************************************************************************
Here is my lsmod :

# lsmod | grep snd
snd_pcm_oss            47648  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                82056  1 snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
snd_opl3_lib           10496  0
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_mpu401_uart         7296  0
snd_rawmidi            23072  1 snd_mpu401_uart
snd_seq_device          8588  2 snd_opl3_lib,snd_rawmidi
snd                    51300  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
*****************************************************************************
Here is my dmesg :

# dmesg | grep es18xx
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/isa/es18xx.c:2204: ESS AudioDrive ES18xx soundcard not found or device busy
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/isa/es18xx.c:2204: ESS AudioDrive ES18xx soundcard not found or device busy
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/isa/es18xx.c:2204: ESS AudioDrive ES18xx soundcard not found or device busy
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/isa/es18xx.c:2204: ESS AudioDrive ES18xx soundcard not found or device busy

---

### Post by mo_x on 2005-07-25
I don't see the es18xx module in the lsmod ouput. Have you tried loading it manually with "modprobe es18xx"?

---

### Post by miguipda on 2005-07-26
In fact due to the fact that as explained I don't have any /dev/dsp and then can't insmod snd-es18xx.
I tried all found information on forums and websites. Nothing changed.

The problem is I don't have any /dev/dsp and then can insmod any driver.

---

### Post by mo_x on 2005-07-26
Some quick searching on google will give a lot of information, try the following link.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

---

