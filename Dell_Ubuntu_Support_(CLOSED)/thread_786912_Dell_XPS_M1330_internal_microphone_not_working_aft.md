---
title: "Dell XPS M1330 internal microphone not working after update to 8.04 Hardy"
date: 2008-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by argotnaut on 2008-05-08
I just updated to 8.04 through system update, and now I get only a hiss from the integrated digital mic. This happens in every program I've tried, from sound recorder to the Flash plugin mic capture.

During the update, I was asked if I should keep the existing /etc/modprobe.d/alsa-base or install the new one. I wasn't sure what to do, so I kept the existing configuration. Was that stupid? :)

Anyone know how I can fix this or other things I need to check first?

Thanks.

---

### Post by eamonireland on 2008-05-12
I have exactly the same problem. I don't remember selecting anything to keep configuration on update. I've tried several solutions suggested in posts, but nothing has worked.

I mainly use my mic for skype, and so I can't use this at all now.

---

### Post by argotnaut on 2008-05-12
Well, here's another clue: I noticed that there was no longer an option to select the source for digital input.

Skype is what I'm using it for too, and I really needed to have things working again. So I gave up, downloaded the Dell Gutsy recovery ISO, and wiped my hard drive. 

The recovery disc wipes out your existing partitions, so if you have a lot of stuff on your hard drive, it might be less time-consuming to install standard Ubuntu and manually do all of the fixes on Dell's wiki. I've only had mine a couple of weeks, so there wasn't anything on here yet that I really needed to save.

---

### Post by brunods on 2008-05-13
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330)

Try this, I'm thinking about buyinf a XPSM1330 and was reading the wiki LaptopTesting.

So, since you have it, how is it? does it handle ubuntu well?

---

### Post by eamonireland on 2008-05-21
I've found it great. I had terrible problems with Vista, and I find everything runs much faster and reliably, plus I've never had problems with my wireless connection, which kept dropping under Vista.

I found your link above very useful. There are small problems that I'll use that forum post to resolve. The touchpad is oversensitive when I'm typing, and after fixing a Hardy introduced error with Skype my volume buttons now don't work (but I can change it using the onscreen volume controls).

---

### Post by bbock on 2008-06-02
While using Ubuntu 7.04, I introduced the following line in /etc/modprobe.d/alsa-base in order to make the mic work (according to [http://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](http://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)).

```

options snd-hda-intel model=3stack

```

This line has to be ***removed*** again in order to make the mic work with 8.04!

---

### Post by keryonic on 2008-06-03
Vostro 1310 is the little brother of the XPS M1330 (hardware is practically identical) and microphone doesn't work either even after wasting hours reading forums and trying different things. I have Ubuntu 8.04. I thought Dell was supporting Ubuntu on XPS M1330 but it seems it only does with 7.10...strange!

---

### Post by Technoviking on 2008-06-03
Adding the Dell PPA and running fixed the problem for me.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by matyasfalvi on 2008-09-25
> Adding the Dell PPA and running fixed the problem for me.

Hi I just added as you told the

```
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

```

line to the sources.list did the 

```
sudo apt-get update
sudo apt-get upgrade
```

my microphone still doesn't work and the media buttons aren't working either as of now.

Does anybody have any suggestions? Please! I am new to Ubuntu and I am pretty confused on how to move on. And thanks very much in advance!

---

### Post by matyasfalvi on 2008-09-25
Hi Mike! 

Could you please help me on this one!

I have a dell xps m1330.

Thanx

---

### Post by matyasfalvi on 2008-09-26
Hi I finally figured out the problem in my case. I hope it helps for some of you:

type in terminal:

```
alsamixer
```

go to the "right" and change input option from analog to digital!

However I still can't work my volume controls on the touch-panel nor with the remote control only the on screen controls work. Anyone any suggestions?

Thanx!

---

### Post by matyasfalvi on 2008-09-26
Hi I figured out what caused the problem with the volume controls sorry I am a beginner here is the resolution if someone has the same problem:

[http://ubuntuforums.org/showthread.php?p=5860780#post5860780](http://ubuntuforums.org/showthread.php?p=5860780#post5860780)

---

### Post by nilbus on 2009-11-07
I had this same problem in Karmic, and this helped fix my mic input. 

Install pavumeter 
```
sudo apt-search install pavumeter
```

Run pavumeter, and change Configuration > Internal Audio Profile to Analog Surround 4.0 Output + Analog Stereo Input.  I don't have surround, but this is the option that allows playback and recording simultaneously for me.

Then go to Input Devices, and slide the Internal Audio Analog Stereo slider from Base to Max. This is necessary because of [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998)

Then follow the instructions below to switch the mic source from analog (mic jack) to digital (internal mic).

> **matyasfalvi said:**
> Hi I finally figured out the problem in my case. I hope it helps for some of you:

type in terminal:

```
alsamixer
```

go to the "right" and change input option from analog to digital!

However I still can't work my volume controls on the touch-panel nor with the remote control only the on screen controls work. Anyone any suggestions?

Thanx!

---

