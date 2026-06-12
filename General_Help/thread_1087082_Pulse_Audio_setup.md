---
title: "Pulse Audio setup"
date: 2009-03-04
forum: General Help
---

### Post by sripplinger on 2009-03-04
I'm having trouble getting pulse audio to work in Kubuntu 8.10.  The only instructions I've found online look to be a bit dated.  I've installed all the pulseaudio applications available using apt-get.  Recently Amarok has not been playing.  I've also found that a few other applications (a couple of games) will not play sound unless I run pulseaudio -D.  I have to run it every time I reboot, too.

If anybody can give me some instructions, point me to another thread, or a webpage, I would appreciate it.

---

### Post by renebs on 2009-03-04
go here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
good luck

---

### Post by sripplinger on 2009-03-05
I've looked at the thread you referred me to, and like all the others I've found the instructions seem specific to gnome, not KDE.  Here is where I get confused:

4. Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "PulseAudio". Close the application when you're finished.

The "System/Preferences/Sound" menu is not the same in KDE.  Either that or I can't find it.  I have found a "Sound" menu under the System Settings menu, but it does not appear to be the same.  Can anybody help me around this one?

---

### Post by SuperSonic4 on 2009-03-05
System Settings --> Multimedia

there it should ask which you device you want to have preference if that's what you mean. Mine has HDA nVidia as number 1 and Pulse Audio as number 2. Also what backends do you have? (it's in the other tab)

---

### Post by sripplinger on 2009-03-05
I don't have a "Multimedia" option, but what you're describing sounds the same as my "Sound" menu.  The instructions said to change the sound capture to PulseAudio, but that is not an available option.  I'm going to see if I get anywhere following the remaining instructions without this step...

---

### Post by Syniurge on 2009-03-06
Yep the old HOWTO is absolutely not required. If you have upgraded to KDE 4.2 (either by enabling the backports or using the experimental repo), the only thing needed to get PulseAudio working within KDE is installing "pulseaudio" in Adept and making "pulse-session" run before KDE launches using this command:

```
cp /usr/bin/pulse-session ~/.kde/env/pulse-session.sh
```

Then after restarting KDE, Phonon devices(not just the "PulseAudio" device) will map to PulseAudio instead of ALSA.

(and if you want to control PulseAudio per-app preferences you might want to install the GUI "padevchooser")

---

### Post by sripplinger on 2009-03-06
That worked perfectly!  Thank you.

---

