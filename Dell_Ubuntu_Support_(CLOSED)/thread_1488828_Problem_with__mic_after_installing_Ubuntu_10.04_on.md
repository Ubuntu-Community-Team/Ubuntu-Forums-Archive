---
title: "Problem with  mic after installing Ubuntu 10.04 on Dell Vostro 1500"
date: 2010-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denverite on 2010-05-20
I installed Ubuntu 10.04 on dell vostro 1500, my mic doesnt work with voice recorder,skype nor anything.
I checked "alsamixer" which didnt help.
I would appreciate if anybody could help me in fixing this.

Cheers!:guitar:

---

### Post by venkidwaraka on 2010-05-21
Please try this and check whether this helps

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Thanks,
Venk!!:)

---

### Post by bubblehead74 on 2010-05-21
You may have already done this, but mic is muted by default in 10.04. You need to go to the sound settings and activate it.

---

### Post by veero on 2010-06-12
i have the same problem. it doesn't matter what version of ubuntu, the external mic can't work properly. sometime i managed to make it work by plugging it in before staring the OS, but anyway it worked occasionaly.
also, all the audio setting is a mess, because for example recordmydesktop won't recognize the mic, simply won't record the audio from whatever i'm doing, and also, the audio it records is weak with white noise interruptions and with a delay audio-video.
i can't understand the utilty of ALSA. so far i know that with dell IT WORKS VERY VERY BAD!
at least music, videos and internet works fine...

---

### Post by CoolJohnB on 2010-07-16
I had the same problem with my Vostro 1700, got it sorted through the general forum if you start in:
_[U]Sorry can't find the thread anywhere here is the code_[/U]:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desptop
sudo apt-get install linux-backports-modules-alsa-lucid-generic

Then reboot

  Then do a search for low mic volume in Skype and you will find further instructions.

My mic works fine now in Skype and very low in Sound Recorder, but as I only use it in Skype everything is good for me.

Hope that helps you.

---

### Post by vangop on 2010-07-31
That helped a bit, now the volume is really low (after installing backports) The mic wasn't working at all on my 1700.. Is there any other magic I need to do afterwards?

---

### Post by easybeat on 2010-08-02
[QUOTE=Then do a search for low mic volume in Skype and you will find further instructions.[/QUOTE]

Could you give me a hint to search what for in Skype Forums? I cannot find any hints what to change...

Thanks

easybeat

---

### Post by vangop on 2010-08-09
Ok, this maybe offtopic, but I managed to increase my internal mic volume (external doesn't work at all) to a good level. 
padevchooser package installed, run the chooser applet, then open manager. 
On the devices tab open the properties of the sources->alsa_..... (Internal audio stereo in the description). There I had 100% volume, but it was only 1/3 of the volume bar. I adjusted to 200% and the volume was good for me.(can increase even more but that's too much)
Hope that helps somebody.
P.S. make sure you uncheck 'allow skype to adjust my mixer levels' as it drops the volume to 100%

---

### Post by CoolJohnB on 2010-08-10
> **easybeat said:**
> Could you give me a hint to search what for in Skype Forums? I cannot find any hints what to change...

Thanks

easybeat

Sorry I meant you to search in this forum for "low mic volume in Skype"  NOT any Skype forum

---

### Post by vangop on 2010-08-12
Just to clarify: are you able to enable external mic, but it's got low volume? My internal works fine now, but external only produces noises.
are you using any hda-intel module specifications in /etc/modprobe.d/alsa-base.conf ?
I have ```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06

```

```

$ tail /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=dell-laptop
```

---

### Post by vijdhasmana on 2010-08-28
> **CoolJohnB said:**
> I had the same problem with my Vostro 1700, got it sorted through the general forum if you start in:
_[U]Sorry can't find the thread anywhere here is the code_[/U]:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get install linux-backports-modules-alsa-lucid-generic

Then reboot

  Then do a search for low mic volume in Skype and you will find further instructions.

My mic works fine now in Skype and very low in Sound Recorder, but as I only use it in Skype everything is good for me.

Hope that helps you.


This worked for me.... thank you

---

### Post by uhurusurfa on 2011-03-07
On a Dell 1721 AMD64 - after install of Ubuntu 10.10 the external jak for the mic did not work. Afer hours of messing about it sems the answer is to install the Alsa mixer GUI front end (Ctk+ version NOT the Gnome one which did nothing at all) then make sure "Capture" buttons are reasonably high up the slider and the £Line Jack Mode" is set to "Mic". Probably there re command line options to do this instead.

---

