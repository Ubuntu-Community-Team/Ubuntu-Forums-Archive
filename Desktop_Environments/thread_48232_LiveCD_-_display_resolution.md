---
title: "LiveCD - display resolution"
date: 2005-07-11
forum: Desktop Environments
---

### Post by mackinax on 2005-07-11
I am trying the Kubuntu 5.04 (i86) LiveCD. I have not much experience using *nix.

The max display resolution option is only 640x480, which is almost unuseable. 

My video card is a Geforce 2 MX PCI. (nvidia / made by hercules)
monitor is a Viewsonic A70 (capable of 1024x768x85 (and higher))

What can I do, either during or post boot, to load a better display driver?

I don't necessarily need Nvidia drivers, just something that will allow greater rez.

Thank you very much!

---

### Post by Umbra on 2005-07-12
[http://www.ubuntuforums.org/showthread.php?t=48334](http://www.ubuntuforums.org/showthread.php?t=48334)

hope that helps.

---

### Post by mackinax on 2005-07-12
[QUOTE=Umbra][http://www.ubuntuforums.org/showthread.php?t=48334](http://www.ubuntuforums.org/showthread.php?t=48334)

hope that helps.[/QUOTE]
Thanks Umbra, I appreciate the reply. :)
I've tried to edit xorg.conf (which is definitely lacking some info), but kedit returns "unknown command" or some such and I can't figure out how else to edit it. I also tried "sudo dpkg-reconfigure xserver-xorg". The hardware seems to be detected correctly, but after the reconfigure, restarting (ctrl+alt+back) yielded no change... (is that even what I should have done?).

Anyhow, now I think I might rather try (and eventually use) it on a different computer. My PII-350, with a 3dfx Voodoo Banshee GPU and an EMC monitor, started up well with all the display rez options offered during hardware detection. The only problem was it didn't detect my **Soundblaster 16 PCI** soundcard.

---

### Post by Umbra on 2005-07-12
Are you testing the distribution? or why r u using the livecd? I dont know, but maybe the livecd doesnt have complete support for some hardware they could be generics.

---

### Post by maruchan on 2005-07-12
> I've tried to edit xorg.conf (which is definitely lacking some info), but kedit returns "unknown command" or some such and I can't figure out how else to edit it. I also tried "sudo dpkg-reconfigure xserver-xorg". The hardware seems to be detected correctly, but after the reconfigure, restarting (ctrl+alt+back) yielded no change... (is that even what I should have done?).

Okay...the first point is important. Exactly what command did you use that didn't work?

As for "the hardware seems to be detected correctly," are you *sure* it picked up your monitor config correctly - the correct refresh rates and everything? 

We really need to look in your xorg.conf to check this.

After that, you won't have this problem again :) I got frustrated with the liveCD at 640 (didn't even try your route), did an HD install, inserted the correct monitor info, and now everything's peachy.

---

### Post by mackinax on 2005-07-13
I'm sorry about my communication not being very clear. 

I initially thought there might be something simple I was overlooking during boot-up, or a quick-n-easy fix. I don't want to waste my - or anyone else's - time any further on this LiveCD run. For now, I think I'll just get by with things as they are, and worry about fine tuning the hardware configuration if/when I decide to do a HDD install. I'm sure we could get any such issues sorted, with your gracious help, at that time.

Thanks again, I really appreciate your kind replies! 
I will probably be back at a later time.  :-D

---

