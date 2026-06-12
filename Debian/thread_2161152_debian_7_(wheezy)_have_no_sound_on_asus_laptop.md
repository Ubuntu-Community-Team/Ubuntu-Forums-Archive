---
title: "debian 7 (wheezy) have no sound on asus laptop"
date: 2013-07-09
forum: Debian
---

### Post by meego on 2013-07-09
debian 7 (wheezy) have no sound on asus laptop,help me please1&#12289;
```
wheezy@debian:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660 Analog [ALC660 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660 Digital [ALC660 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #02
```
&#12289;then
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
 then add
```
options snd-hda-intel model=3stack-660 3
```
&#12289;then
```
killall pulseaudio
```
```
wheezy@debian:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq snd-seq-device snd-timer.
```
4&#12289;
```
wheezy@debian:~$ pulseaudio -D
E: [pulseaudio] main.c: &#21518;&#21488;&#31243;&#24207;&#21551;&#21160;&#22833;&#36133;&#12290;
```
5&#12289;
```
wheezy@debian:~$ sudo ls -la /dev/snd
total 0
drwxr-xr-x   3 root root      260  7&#26376;  9 20:53 .
drwxr-xr-x  14 root root     3220  7&#26376;  9 22:16 ..
drwxr-xr-x   2 root root       60  7&#26376;  9 20:53 by-path
crw-rw---T+  1 root audio 116,  9  7&#26376;  9 20:53 controlC0
crw-rw---T+  1 root audio 116,  8  7&#26376;  9 20:53 hwC0D0
crw-rw---T+  1 root audio 116,  7  7&#26376;  9 20:53 hwC0D1
crw-rw---T+  1 root audio 116,  6  7&#26376;  9 22:26 pcmC0D0c
crw-rw---T+  1 root audio 116,  5  7&#26376;  9 22:26 pcmC0D0p
crw-rw---T+  1 root audio 116,  4  7&#26376;  9 22:26 pcmC0D1p
crw-rw---T+  1 root audio 116,  3  7&#26376;  9 20:53 pcmC0D6c
crw-rw---T+  1 root audio 116,  2  7&#26376;  9 20:53 pcmC0D6p
crw-rw---T+  1 root audio 116,  1  7&#26376;  9 22:27 seq
crw-rw---T+  1 root audio 116, 33  7&#26376;  9 20:53 timer
```
6&#12289;
```
wheezy@debian:~$ groups
wheezy cdrom floppy audio dip video plugdev scanner bluetooth netdev
```
7&#12289;
```
wheezy@debian:~$ alsamixerall right
```
8&#12289;
```
root@debian:~# alsactl init
Found hardware: "HDA-Intel" "Realtek ALC660" "HDA:10ec0861,10431105,00100340 HDA:10573055,104310c6,00100700" "0x1043" "0x1263"
Hardware is initialized using a generic method
```
debian 7 (wheezy) have no sound on asus laptop,have reset a lot of times ,please help ,thanks a lot!

---

### Post by duanedesign on 2013-07-09
you might see if you can edit this question to make it easier to read.

---

### Post by pqwoerituytrueiwoq on 2013-07-09
I fixed up the 1st post
> **meego said:**
> debian 7 (wheezy) have no sound on asus laptop,help me please1&#12289;
```
wheezy@debian:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660 Analog [ALC660 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660 Digital [ALC660 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #02
```
&#12289;then
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
 then add
```
options snd-hda-intel model=3stack-660 3
```
&#12289;then
```
killall pulseaudio
```
```
wheezy@debian:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq snd-seq-device snd-timer.
```
4&#12289;
```
wheezy@debian:~$ pulseaudio -D
E: [pulseaudio] main.c: &#21518;&#21488;&#31243;&#24207;&#21551;&#21160;&#22833;&#36133;&#12290;
```
5&#12289;
```
wheezy@debian:~$ sudo ls -la /dev/snd
total 0
drwxr-xr-x   3 root root      260  7&#26376;  9 20:53 .
drwxr-xr-x  14 root root     3220  7&#26376;  9 22:16 ..
drwxr-xr-x   2 root root       60  7&#26376;  9 20:53 by-path
crw-rw---T+  1 root audio 116,  9  7&#26376;  9 20:53 controlC0
crw-rw---T+  1 root audio 116,  8  7&#26376;  9 20:53 hwC0D0
crw-rw---T+  1 root audio 116,  7  7&#26376;  9 20:53 hwC0D1
crw-rw---T+  1 root audio 116,  6  7&#26376;  9 22:26 pcmC0D0c
crw-rw---T+  1 root audio 116,  5  7&#26376;  9 22:26 pcmC0D0p
crw-rw---T+  1 root audio 116,  4  7&#26376;  9 22:26 pcmC0D1p
crw-rw---T+  1 root audio 116,  3  7&#26376;  9 20:53 pcmC0D6c
crw-rw---T+  1 root audio 116,  2  7&#26376;  9 20:53 pcmC0D6p
crw-rw---T+  1 root audio 116,  1  7&#26376;  9 22:27 seq
crw-rw---T+  1 root audio 116, 33  7&#26376;  9 20:53 timer
```
6&#12289;
```
wheezy@debian:~$ groups
wheezy cdrom floppy audio dip video plugdev scanner bluetooth netdev
```
7&#12289;
```
wheezy@debian:~$ alsamixerall right
```
8&#12289;
```
root@debian:~# alsactl init
Found hardware: "HDA-Intel" "Realtek ALC660" "HDA:10ec0861,10431105,00100340 HDA:10573055,104310c6,00100700" "0x1043" "0x1263"
Hardware is initialized using a generic method
```
debian 7 (wheezy) have no sound on asus laptop,have reset a lot of times ,please help ,thanks a lot!
on 4 it would say "*Daemon startup failed.*" if the OP was using the English version
and on 5 [FONT=Courier New]7&#26376;[/FONT] would be [FONT=Courier New]July[/FONT]

---

### Post by meego on 2013-07-10
1&#12289;options snd-hda-intel model=3stack-660        after the last word ,not have 32&#12289;I use the command wheezy@debian:~$ alsamixerall&#65292;it pop up the Adjustment button all right

---

### Post by meego on 2013-07-10
debian 7 (wheezy) have no sound on asus laptop&#65292;I have tried a lot of ways ,but it doesn't work,please help me.

---

### Post by wtheron on 2013-11-22
I had a similar problem after installing Wheezy.  Perhaps my solution may come in handy to others.  

> debian@wheezy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I previously had a graphics problem (on the first Wheezy release) and someone suggested that I should try a more updated kernel by installing a backport. This not only solved my graphics problem with my Haswell chipset, but the latest backport 3.10 fixed my sound issues as well.  

First, you need to add the backport repository to your sources.list and reload your repository
> 
echo "deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) wheezy-backports main"  >> /etc/apt/sources.list && apt-get update

You then need to search for the available backports.  You can see the list by typing

> apt-get search linux-

Since I have an AMD64, I opted for the 3.10-0.bpo.3-amd64 releases.  You need both the image file and the associated headers, enter.

> aptitude -t wheezy-backports install linux-image-3.10-0.bpo.3-amd64

for the image file, and
> 
aptitude -t wheezy-backports install linux-headers-3.10-0.bpo.3-amd64 

for the headers.  Grub will automatically update.  When you restart, you can pick the latest kernel.  For some reason, alsamixer defaulted to my hdmi, so I had to make a change to the config.  I created the config file

~/.asoundrc

with the following entry

> pcm.!default {
        type hw
        card 1
}

ctl.!default {
       type hw
       card 1
}

When I restarted, running alsamixer showed the desired controls I wanted.  Hope this helps.

---

