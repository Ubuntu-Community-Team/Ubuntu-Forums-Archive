---
title: "PCSX-Reloaded sound is choppy in Silent Hill"
date: 2012-04-05
forum: Emulators
---

### Post by gurokko on 2012-04-05
Does anyone have any advice...?  I'm running Ubuntu 11.10 with the GNOME3 desktop (I do have Xfce installed and also use it on occasion, though.)  Everything else seems to run perfectly, but, for some reason, I can't make the sound any less choppy.  I've googled and googled and tried all kinds of configurations (I'm using the SDL Sound 1.6.0 plugin that comes with my download of PCSX-R and the preset GPU plugin, as well) and nothing has helped.  I also tried turning off pulseaudio, no dice.

Anyone here have any ideas...?  Maybe a different plugin I could try?  Or, hey, I'd be down with trying a whole other emulator, if you have any suggestions.  (I've tried eSPXe and it doesn't play well with my setup, for some reason.)

Thanks for your time.

ETA: I tried the Eternal SPU plugin in the Windows version of PCSX-R, through Wine, and it works flawlessly, but my controller hates Wine.  I tried using the same plugin's linux port in the linux version of PCSX-R, and it... doesn't even show up on the dropdown menu for the sound plugin.  Um... what do I do?

---

### Post by Majorix on 2012-04-05
Try PSP. It is the best PSX emulator :)

---

### Post by gurokko on 2012-04-05
PSP?  I'm not sure what you mean.  As in the portable Playstation system, or is that the name of an emulator?  And if it is the name of the system, that is absolutely NOT in my budget right now, unfortunately.  :(

---

### Post by RJARRRPCGP on 2012-04-05
> **gurokko said:**
> Does anyone have any advice...?  I'm running Ubuntu 11.10 with the GNOME3 desktop (I do have Xfce installed and also use it on occasion, though.)  Everything else seems to run perfectly, but, for some reason, I can't make the sound any less choppy.  I've googled and googled and tried all kinds of configurations (I'm using the SDL Sound 1.6.0 plugin that comes with my download of PCSX-R and the preset GPU plugin, as well) and nothing has helped.  I also tried turning off pulseaudio, no dice.



I dunno. I would try another audio plugin.

---

### Post by gurokko on 2012-04-05
> **RJARRRPCGP said:**
> I dunno. I would try another audio plugin.

This is a good idea, and I'm trying to, but for some reason, my emulator refuses to recognize any other plugins.  They don't even show up on the dropdown menu.  Am I putting them in the wrong folder or something?  (I'm putting them in the plugins folder in .pcsx off my home folder.)

---

### Post by gurokko on 2012-04-06
... welp, seems I figured out the problem: I uninstalled and reinstalled PCSXR from the repo instead of from the software manager, and it works perfectly just with the default plugins.  IGNORE ME, I'M A MORON...

---

### Post by RJARRRPCGP on 2012-04-06
> **gurokko said:**
> This is a good idea, and I'm trying to, but for some reason, my emulator refuses to recognize any other plugins.  They don't even show up on the dropdown menu.  Am I putting them in the wrong folder or something?  (I'm putting them in the plugins folder in .pcsx off my home folder.)

Likely dependency-hell. I bet you there's a library error when launched from the terminal and going to the plugin configuration section. 
Especially the dreaded "cannot load shared library file x No such file or directory" error message.

---

