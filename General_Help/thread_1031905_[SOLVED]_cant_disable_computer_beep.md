---
title: "[SOLVED] cant disable computer beep"
date: 2009-01-05
forum: General Help
---

### Post by orlox on 2009-01-05
I cant seem to completely disable the pc speaker from my laptop. I already putted "blacklist pcspkr" on /etc/modprobe.d/blacklist, and this took off a lot of the beeping, but I still get a beeping sound when using the multimedia keys (for instance, if I change the volume with the multimedia keys, i get this annoyng bip!)

Im not sure if the sound is actually from the speaker, because the kernel module for that is disabled...Any ideas??

---

### Post by tuxxy on 2009-01-05
There should be a third tab in your system > prefs > sound for the system beep, you would normally be able to disable it here but this currently an issue with Ibex see link below;

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/282906](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/282906)

---

### Post by pyromanic123boom on 2009-01-05
Some are in system preferences, however, it sounds like the one you're talking about is the awful system beep. That's in the bios when you boot.

---

### Post by Ahadiel on 2009-01-05
> **orlox said:**
> I cant seem to completely disable the pc speaker from my laptop. I already putted "blacklist pcspkr" on /etc/modprobe.d/blacklist, and this took off a lot of the beeping, but I still get a beeping sound when using the multimedia keys (for instance, if I change the volume with the multimedia keys, i get this annoyng bip!)

Im not sure if the sound is actually from the speaker, because the kernel module for that is disabled...Any ideas??

Do you have an HP laptop by chance? If so, there should be an option in your BIOS to disable beeping when pressing multimedia keys.

---

### Post by orlox on 2009-01-06
> Do you have an HP laptop by chance? If so, there should be an option in your BIOS to disable beeping when pressing multimedia keys.

Thats right! I have an hp Pavilion. Ill look for that later and tell you how t went.

---

### Post by bukwirm on 2009-01-06
On my laptop, I can run aumix (used to adjust the audio mixer) and adjust the volume of the "Spkr" channel to adjust the volume of the system beep.

---

### Post by orlox on 2009-01-07
As mentioned by Ahadiel, all I had to do was disable the speaker sound for multimedia keys on the BIOS. Cant imagine who in gods name thought it was reasonable to make the multimedia keys beep directly as a BIOS response :P

---

