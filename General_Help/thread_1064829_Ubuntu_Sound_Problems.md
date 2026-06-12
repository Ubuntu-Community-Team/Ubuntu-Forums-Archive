---
title: "Ubuntu Sound Problems?"
date: 2009-02-09
forum: General Help
---

### Post by yusuo85 on 2009-02-09
Im hating pulse audio, the ability to play audio from one source at anyone time is really annoying. I know there is a fix to switch default audio control back to alsa but I cant remember how to do it and cant find anything on google.
Can anyone help im fed up of every program locking up if I try to play multiple audio

---

### Post by yusuo85 on 2009-02-09
Im really fed up with pulseaudio and the lack of multiple sound sources, is there anyway I can change it back to alsa. im using 8.04-2

---

### Post by gettinoriginal on 2009-02-09
System, Preferences, Sound, Change to Alsa

---

### Post by jonlemur on 2009-02-09
It looks like that can be done from the Volume Control (I don't know if it would have to be done every time you restart the computer).  Applications->Sound & Video->Volume Control  Devices
If Volume Control isn't there, you may have to enable it by right-clicking on the Applications button and selecting Edit Menus, or just run ```
gnome-volume-control
```

---

### Post by kostkon on 2009-02-09
Have you tried to better setup your *PulseAudio* by following [this guide]("http://ubuntuforums.org/showthread.php?t=789578")? *PulseAudio* is not setup the right way in 8.04. I would recommend you to give it a try...

Also, you need to remove *Flash 9* because it causes problems and install *Flash 10*.

To do it, first of all, go to *System &#8594; Administration &#8594; Software Sources* and make sure that in the *Third-Party Applications* tab the *Partner* repository is enabled. If not, then enable it. Press *Close*.

Then open *Synaptic* and search for the *flashplugin-nonfree* (this is *Flash 9*) package and remove it completely (i.e. select the *Complete Removal* option). Then, search for the *adobe-flashplugin* (this is *Flash 10*) and install it.

---

### Post by bapoumba on 2009-02-09
Threads merged.

---

