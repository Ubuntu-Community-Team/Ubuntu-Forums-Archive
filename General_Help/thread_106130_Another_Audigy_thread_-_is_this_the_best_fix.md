---
title: "Another Audigy thread - is this the best fix?"
date: 2005-12-19
forum: General Help
---

### Post by Rushedman on 2005-12-19
Greetings all - first post - second whole day using Kubuntu, my first Linux OS - and I'm liking all kinds of things. But I'd really love to get the Audigy Value card I have to work here - working at the PC without music just blows.

So - this is the process I've taken so far.

 - I've dinked around quite a bit with the Sounds / Multimedia section, trying various combinations, without success. 
 - Checked out all the updates I can get with Synaptic
 - Bugged a buddy of mine locally who's a Ubuntu freak - he's not up on this.
 - Read up on ALSA a good bit.. and found this link.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1)

... but it's a little on the interesting side. And I had to get the compilers to be installed first. (Fortunately, another site had details on getting gcc to work.) 

So I'm still wondering - is there an easier way to do this? Or am I going to learn more about compiling than I wanted to at this very nooob stage?

Thanks!

---

### Post by amohanty on 2005-12-20
1. Do you have onboard audio, ie did the mobo come with audio?
2. Do you have libesd-alsa package (name might be slightly different - dont have access to ubuntu right now)
3. Do you see your device in System->Preferences->Sound
4. Is the sound server checkbox checked in panel in (3)
5. Can you see the card via > lspci


AM

---

### Post by Rushedman on 2005-12-20
The mobo is an Asus A7N8X-X, so yes to the onboard sound.

Dunno about that package, but it'll be on there shortly...

I do see that device.

Panel 3 is... where?

And I'll run the lspci when I check the said package... shortly...

---

### Post by Rushedman on 2005-12-20
Annnd now that I can look at it - it does definitely see the onboard sound, but the Audigy card it doesn't seem to know very well - 

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

0000:01:09.0 Multimedia audio controller: Creative Labs: Unknown device 0008

Interesting... I'll have to dig for getting the system to re-scan the PCI bus... hrrmmmm...

---

### Post by amohanty on 2005-12-20
In your BIOS disable onboard audio.
> Panel 3 is... where?
I mean the dialog in item #3

lspci enumerates all devices the OS sees on the PCI bus. 

to install the package do:
> sudo apt-get install libesd-alsa0

Then do a :
> killall esd

Now if you do a :
> esd &

do you hear a tinkle?

HTH

---

### Post by Rushedman on 2005-12-21
That was it - MIDI doesn't work, but as long as I don't need that for games (going to try installing NWN eventually), I'm very good. Thank you VERY much! :smile:

---

### Post by erikpiper on 2005-12-26
Automatix can install MIDI support if you want, and I think there is an official kubuntu version now!!

BTW, automatixdoes a LOT more than that, but you dont have to use it all..

[http://ubuntuforums.org/showthread.php?t=105343](http://ubuntuforums.org/showthread.php?t=105343)

That was the Kubuntu version. It may seem a tiny bit complex, but the instructions are exact, so it is easy!

---

