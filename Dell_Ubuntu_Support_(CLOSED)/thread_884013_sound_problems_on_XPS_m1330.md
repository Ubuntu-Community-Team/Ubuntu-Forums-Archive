---
title: "sound problems on XPS m1330"
date: 2008-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rabbot on 2008-08-08
for some reason i can't get sound off my dell xps m1330. everything else seems to work fine except that. is there some kind of extra driver i would need to install?

---

### Post by peanut butter on 2008-08-09
Which version of ubuntu are you using? (8.04 introduced a new sound system, pulseaudio,  which can get messed up sometimes) and what are you not getting sound from?

---

### Post by rabbot on 2008-08-10
> **peanut butter said:**
> Which version of ubuntu are you using? (8.04 introduced a new sound system, pulseaudio,  which can get messed up sometimes) and what are you not getting sound from?

the speakers in general. i have no sound coming out of the computer. it works well on vista and yes i am using 8.04.

---

### Post by jbor7755 on 2008-08-24
You aren't the only one. I've just got my XPS set up with XP and Kubuntu 8.04.1 64bit and I can't hear a thing. I'll post back what i can find...

---

### Post by peanut butter on 2008-08-24
one of you who is having this problem, can you please try the following from terminal

killall pulseaudio

and see if you can get sound to play. (try audacity or vlc (with the alsa sound backend))
if that works, then there is obviously a problem with pulseaudio, otherwise, it could be a driver problem. (Intel HDA audio is a bit well known for these types of problems.)

---

### Post by jbor7755 on 2008-08-24
I never had pulse audio installed in the first place... Would this be a problem?

I have tried compiling the latest alsa drivers from source but to no avail

---

### Post by jberger on 2008-08-25
Just want to add that I have the same problem on my M1330!

---

### Post by Crafty Kisses on 2008-08-30
Post the results of > lspci

---

### Post by x001 on 2008-08-30
> **jbor7755 said:**
> I never had pulse audio installed in the first place... Would this be a problem?

I have tried compiling the latest alsa drivers from source but to no avail

From what I understand PulseAudio is installed by default on 8.04. I have XPS1530 and installed 8.04. Sound does not work on Autodetect or on PulseAudio Server but if I select ALSA then it works. Anyone have any ideas how to fix it?

---

### Post by x001 on 2008-08-30
Fixed it on my XPS1530 system. I added the Dell repo information and performed a system upgrade:

Repo:
```

deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

```
then performed
```

$ sudo apt-get update
$ sudo apt-get upgrade

```

more info available @ [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry)

---

### Post by TimDaniels on 2008-09-01
> **x001 said:**
> I added the Dell repo information and performed a system upgrade

How does one perform a system upgrade?

*TimDaniels*

---

### Post by x001 on 2008-09-01
All I did was:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

---

### Post by TimDaniels on 2008-09-01
> **x001 said:**
> All I did was:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

For the other sufferers of no sound on their XPS-M1330, I tried essentially that, as guided by the instructions at
**[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry)** and
**[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work)**,
but there has been no return of sound to the laptop.

*TimDaniels*

---

### Post by TimDaniels on 2008-09-03
> **rabbot said:**
> for some reason i can't get sound off my dell xps m1330. everything else seems to work fine except that. is there some kind of extra driver i would need to install?

See the thread "another 'no sound' - M1330" ([http://ubuntuforums.org/showthread.php?t=906958](http://ubuntuforums.org/showthread.php?t=906958)).  The solution for my M1330 was to clear the ALSA (Advanced Linux Sound Architecture) configuration files ```
sudo /etc/init.d/alsa-utils stop
sudo rm /var/lib/alsa/asound.state
sudo /etc/init.d/alsa-utils start
``` and to configure the existing panels accessible via the speaker icon (see my reply in thread "M1530 Sound Trouble" - [http://ubuntuforums.org/showthread.php?t=909173](http://ubuntuforums.org/showthread.php?t=909173)).

*TimDaniels*

---

