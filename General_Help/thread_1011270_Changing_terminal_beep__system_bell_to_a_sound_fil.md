---
title: "Changing terminal beep / system bell to a sound file"
date: 2008-12-14
forum: General Help
---

### Post by BattlePanic on 2008-12-14
I am using 8.10 Intrepid and I have been trying to find a way of replacing the beep from my pc speaker with the playback of a sound file.  I use gnome-terminal and this is really the only program where I want such functionality.  Ideally, I'd like to just mute my PC speaker via the ALSA mixer and have the system bell sound handled by my sound card.

Looking under System -> Preferences -> Sound shows that the "Play alert sound" option is checked but the associated sound file doesn't seem to be used by gnome-terminal.

Running gconf-editor and looking under desktop -> gnome -> peripherals -> keyboard shows two settings which look interesting.  "bell_custom_file" and "bell_mode".  Switching "bell_mode" to the value "custom" and setting the value of "bell_custom_file" to "/usr/share/sounds/ubuntu/stereo/bell.ogg" doesn't seem to do anything though.

Any thoughts or ideas on this one?

---

### Post by mwshook on 2008-12-15
I'm having the same issue. All other sound functions seem to work fine, but any error message box, or event on gnome-terminal causes a PC speaker beep.

---

### Post by InuY4sha on 2009-01-24
Same is happening to me... quite odd and annoying..

---

### Post by d4rk_rebel on 2009-08-09
I have been working on this all day and can't get it to work.  Let me know when someone finds a fix.

---

### Post by Post Monkeh on 2009-08-09
do what i did and turn off your pc speaker in the bios

---

### Post by skb on 2009-08-09
You can disable the pc speaker using "sudo rmmod pcspkr" without having to go into your BIOS. The reverse would be "sudo modprobe pcspkr".

---

### Post by Post Monkeh on 2009-08-10
> **skb said:**
> You can disable the pc speaker using "sudo rmmod pcspkr" without having to go into your BIOS. The reverse would be "sudo modprobe pcspkr".
Does this do the same as disabling it in the bios or is it only within ubuntu that it would be disabled?

---

### Post by mcduck on 2009-08-10
> **skb said:**
> You can disable the pc speaker using "sudo rmmod pcspkr" without having to go into your BIOS. The reverse would be "sudo modprobe pcspkr".

Of course that's just a temporary solution, and will reset as soon as you reboot the system.

To make the change permanent you have to blacklist the pcspkr module in /etc/modprobe.d/blacklist.conf. (You can also create your own blacklist file in the smae directory if you don't want to touch the system files).

And yes, this will only disable the beeper in Ubuntu. Operating system's don't have  any control over your BIOS settings or other operating systems installed in the same machine. If you want to disable the beeper in a way that affects all installed systems, you need to do it in BIOS, or by physically disconnecting the speaker (which is, at least with desktop systems, very simple to do; just unplug the speaker's wires from your motherboard's connector).

---

### Post by martinbaselier on 2009-08-10
only within ubuntu

---

