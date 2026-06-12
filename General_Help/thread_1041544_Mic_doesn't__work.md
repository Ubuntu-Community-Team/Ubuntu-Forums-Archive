---
title: "Mic doesn't  work"
date: 2009-01-16
forum: General Help
---

### Post by banana jama on 2009-01-16
i using a hp pavilion dv6000 that has built in mics but ubuntu does't doesn't seem to recognize them. at first i thought it was skype but when i use sound record the mic doesn't work either. how do i get my mics to work. i don't know what model they are since they are built into my laptop.

---

### Post by banana jama on 2009-01-16
bump

---

### Post by gettinoriginal on 2009-01-16
First, right click your sound icon on the panel, select open volume control and make sure that your mic is not muted.  If that is ok, then here are some sites that may help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by banana jama on 2009-01-16
my mic isn't muted and it seems that the os recognizes that a mic exsits  but there still doesn't work. thanks for the links but i've looked over some of there suggestions but it doesn't seem to work. the first link talks about sound cards (which i have no problems with) and the rest talks about pulse audio in specific no sound (i have sound just not the ability to use my microphone). 
 this is the out put from sudo amixer

> Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]


---

### Post by banana jama on 2009-01-19
i've been messing aroud in the terminal and this came up when i put pulseaudio mixer. 

```
akeem@akeem-laptop:~$ sudo  pulseaudio mixer
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_55c_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Cannot find fallback mixer control "Mic".

```

it says something about  the mic not being found. is there anyway that i can get pulseaudio to recognize the mic? any suggestion would be appreciated

---

### Post by gettinoriginal on 2009-01-19
in applications > sound/video > there should be a Pulseaudio Device Chooser, it will bring up an applet in your notification area, click on that and set your devices.  If it is not there, go to Synaptic and install:
> padevchooser

---

### Post by banana jama on 2009-01-19
ok thanks so i just downloaded the app you told me to download but i don't know what you mean by set your device. when i click on the app and go to preferences it says "currently there is no device playing audio" and "currently there is no device recording audio".

---

### Post by gettinoriginal on 2009-01-19
Go above preferences, headphones (speakers), microphone, and set there.

---

### Post by banana jama on 2009-01-19
i think it set the devices automatically when i downloaded pulseaudio. it recognize my microphone (i know this because it list it in volume meter record) but when i use sound recorder it still doesn't record anything.

---

### Post by gettinoriginal on 2009-01-19
right click your sound icon on the panel.  Open volume control, switches, make sure mic and mic boost are checked.

---

### Post by banana jama on 2009-01-19
i didn't see mic and mic boost under switces all i seen was something called IEC958 AND IEC958 DEFAULT PCM i checked them both off but still no luck.

i've notice when i go to manager and click on devices it has one thing under sink that has the word playback in it but, under sources it shows two things one with the word playback and the other with the word capture.
does this mean pulse audio still hasn't recognize the mic?

---

### Post by banana jama on 2009-01-19
.

---

### Post by gettinoriginal on 2009-01-19
Wow, getting worse instead of better :confused:  System, Preferences, Sound, how is yours set up ??

[ATTACH]100431[/ATTACH]

---

### Post by banana jama on 2009-01-19
i've got my speakers back after i restarted my computer. mine looks like this:

---

### Post by banana jama on 2009-01-19
i've notice when i set mine up how you have yours set up im able to get static when i record something in sound recorder ( i don't know if this means anything)

---

### Post by banana jama on 2009-01-19
ok major head way has been made. my mics work a little. it cannot pick up my voice but when i play a song on my laptop it picks the up barely and there is a huge amount of static. i've turned up the mics all the way but the problem still persists. does anyone know how i can get the mics to pic up MY VOICE and decrease the amount of static?

---

### Post by gettinoriginal on 2009-01-19
In looking at your settings above, your sound capture is listed as analog, do you have a digital option ??

---

### Post by banana jama on 2009-01-19
no there is no digital option these are the only options :

---

### Post by banana jama on 2009-01-19
a bump a bump bump

how do you gain digital options in sound capture?

---

### Post by Ketara on 2009-01-26
I'd just like to throw out that I'm having the exact same problem, also with an HP laptop.

Intrepid will not recognize either the internal or an external mic, and I can't even get the sound tab in preferences to play test sounds in the sound capture field.

No other audio issues anywhere.

---

### Post by tim183 on 2009-03-22
same problems here. as at janty alpha 6 it persists.

---

