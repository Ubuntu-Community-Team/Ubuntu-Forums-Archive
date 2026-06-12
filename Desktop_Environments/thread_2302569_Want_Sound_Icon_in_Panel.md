---
title: "Want Sound Icon in Panel"
date: 2015-11-11
forum: Desktop Environments
---

### Post by Rick St. George on 2015-11-11
When I pull down Panel Preferences in UbuntuStudio, I have "Indicator Plugin" and within that I have "Sound Menu".
This puts a speaker icon in the menu bar giving quick access to adjust audio properties, also when clicking the icon there is a shortcut to "Audacious" if installed.

But in Xubuntu, while there is an "indicator plugin", there is no "sound menu" within.
Is there a way to add it? It does not appear so within as it only shows these 3 items;
  "App indicators", "Power Mgmt", and "Messaging Menu".

I would like to see the "speaker" icon in Xubuntu.
Thanks for any help! Any ideas?

Rick
):P

---

### Post by Dennis N on 2015-11-11
Some possible things to try:
Check to see that **indicator-sound** is installed. (It should be installed by default). Install if somehow missing. 
Reinstall indicator-sound if already installed. Reboot.

*My system: Xubuntu 15.10*

---

### Post by Rick St. George on 2015-11-11
Pardon my ignorance, but how do I do that?

---

### Post by Dennis N on 2015-11-11
> **Rick St. George said:**
> Pardon my ignorance, but how do I do that?

You can use the terminal with the command **apt-cache policy indicator-sound**

```
dmn@Zotac:~$ apt-cache policy indicator-sound
indicator-sound:
  Installed: 12.10.2+15.10.20150915-0ubuntu1
  Candidate: 12.10.2+15.10.20150915-0ubuntu1

```

If it is not installed, it will report "none"

---

### Post by Rick St. George on 2015-11-11
I get;

Installed:  (none)
Candidate: 12.10.2+14.04.20140401 -0ubnut1
Version Table:
   12.10.2+14.04.20140401 -0ubuntu1 0
   500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
   100 /var/lib/dpkg/status

Also, under "Session and Starup / Application Autostart"  it shows "Indicator Sound" and is checked!

What does this mean?
Thanks DennisN !

---

### Post by Dennis N on 2015-11-11
I would install it since it is missing:

```
sudo apt-get install indicator-sound

```

Also a reboot after install is complete may be needed.

---

### Post by Rick St. George on 2015-11-11
Installed and Rebooted.

BAM - Icon shows!  However, when I click on "sound settings" nothing comes up. For some reason, it must not be linked to PulseAudio.

Not a big thing, but if you have a suggestion, I will check it.  Thanks a Million ... I love Ubuntu. Yesterday played with Win7 to get Acrobat loaded ... failed 6 times, tried to print - had to reinstall what was already installed. Reboot to linux - plugged in printer ... Presto, ready to print. No Problem. I love it when a plan comes together.

Rick

---

### Post by Dennis N on 2015-11-11
Do you have pulseaudio volume control  (pavucontrol) installed? Again, it should be installed by default, but might be missing like your indicator-sound.

```
dmn@Zotac:~$ apt-cache policy pavucontrol
pavucontrol:
  Installed: 3.0-3build1
  Candidate: 3.0-3build1

```

Those settings are also accessible from the Xubuntu **Main menu > multimedia > PulseAudio Volume Control**

---

### Post by Rick St. George on 2015-11-11
YES - it shows 2.0-2

---

### Post by Dennis N on 2015-11-11
Well, you could:

1) Leave things as they are and use the Main (Whisker) Menu entry to adjust Pulse Audio Volume Control settings.
2) Put a launcher on your panel for Pulse Audio Volume Control if you access it a lot and don't want to go through the a menu.
3) Reinstall pavucontrol and see if that creates the linkage.  

(I go to Whisker Menu's entry myself. It's just as easy as opening the sound menu, which I always forget has that link at the bottom.)

---

### Post by Rick St. George on 2015-11-11
No. 3 didn't work, but ... Such a minor issue, I will consider this closed.
Thanks Dennis .. your the Man ! ! !

Rick

---

