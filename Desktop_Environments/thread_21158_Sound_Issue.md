---
title: "Sound Issue"
date: 2005-03-20
forum: Desktop Environments
---

### Post by macmasterxiv on 2005-03-20
I just did a clean install of the hoary preview for amd64. I was amazed at how well the sound worked in this release. It seems I have spoken too soon, however. After enabling universe and installing a few packages (none of which should have done this, except maybe the kernel) and when I booted up, I had no sound whatsoever. Alsamixer says no sound elements found and all the programs I've tried can't access sound. The gnome volume control, however, says the volume is normal and working. For what it's worth, I have an nf3 motherboard with the Realtek ALC850 chipset (I believe.) Any ideas on how to fix this?

---

### Post by malegria on 2005-03-21
I'd say that the module for your soundcard(onboard) got nicked when you put in the new kernel. If you can, run ```
sudo alsaconf
```

Then restart the computer.

After having done so run ```
alsamixer
``` and move all the sliders to see what then produces sounds. Once you've set to your liking run:```
sudo alsactl store
``` 

This will store the setting for the next boot. I hope this works for you.

---

### Post by macmasterxiv on 2005-03-21
well, I tried running alsaconf, and it says specify command, I've looked at the commands, and none I've tried bring the soundcard back up. I also can't seem to find the driver I was using in any of the modules folders (old or current) does this mean I have to manually build my kernel from source?

---

### Post by malegria on 2005-03-21
What I'd say to do is get the ALSA drivers & utils from their website.[HTML]http://www.alsa-project.org/[/HTML] and build those. Don't touch the kernel. Some dependencies you'll need to compile these will include. gcc (and the dev packages), libasound (and the dev package), and ncurses. I think that's about it. Before you compile the alsa drivers, run ```
./configure --help
```  and see if you see your card'ss name amongst the list. If the name is not there then search their website, sometimes the names are different. For example my AudigyLS is actually listed as ca0106.

Once you compile and install both run ```
sudo alsaconf
``` and reboot. And then follow the instructions as I put them, this should surely fix your problems.

---

### Post by macmasterxiv on 2005-03-21
ok, I overlooked the driver and it's still installed. I installed alsaconf and it ran properly, but when I ran alsamixer, I still get: No mixer elems found

---

