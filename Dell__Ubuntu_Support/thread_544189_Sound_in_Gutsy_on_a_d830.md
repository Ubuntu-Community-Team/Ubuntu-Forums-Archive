---
title: "Sound in Gutsy on a d830"
date: 2007-09-06
forum: Dell  Ubuntu Support
---

### Post by hscott on 2007-09-06
I recently installed Gutsy on my d830 dell and was pleased that the Video worked out of the box.  But the sound hasn't worked yet.  I followed the directions here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")
but was not able to get the sound working I also have it starting in the modules file I know that the driver is trying to install but it is failing here is the error message in dmesg.

[   15.464000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   15.464000] snd_hda_intel: Unknown symbol snd_ctl_add
[   15.464000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   15.464000] snd_hda_intel: Unknown symbol snd_card_register
[   15.464000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   15.464000] snd_hda_intel: Unknown symbol snd_card_free
[   15.464000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   15.464000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   15.464000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   15.464000] snd_hda_intel: Unknown symbol snd_ctl_find_id

Any help would be appreciated

---

### Post by bimbo on 2007-09-06
Did you per chance update your kernel and not recompile the modules? Or compiled them for the wrong kernel version?

---

### Post by geppz on 2007-09-06
With my D830 64bit Gutsy, from tribe-4 and up to a few days ago only headphones were working. With yesterday's apt-get dist-upgrade also speakers work. Sound works up to the first suspend. After a suspend you have to unload the snd_hda_intel module (terminate kmix and any application using sound to be able to do this) and then modprobe it again and restart the sound applications. The speakers will get disabled if the headphones are inserted at boot time or at the last time you have reloaded the snd_hda_intel, speakers will not be disabled if you insert the headphones at any other time. External microphone doesn't work, embedded microphone works though. Test microphone with the vumeter of Audacity, it's the most comfortable way.
I am using 2.6.22-10-generic #1 SMP --- x86_64 GNU/Linux.

---

### Post by bimbo on 2007-09-06
You might want to try adding snd_hda_intel to the modules variable in /etc/acpi/acpi-support to have it automatically unloaded before suspend and reloaded thereafter?

On my x86 Gutsy with handcompiled ALSA I always get sound after resume without any messing around. The headphones do shutoff the speakers, but the headphone port at the docking station behaves erratically wrt to that.

---

### Post by geppz on 2007-09-06
What is that acpi-support? I don't have it. Also, wouldn't there be problems in automatic unload? I assume the unload wouldn't work if any sound application like kmix is running.

Re: hand compiled: Interesting, do you have this exact sound card?
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
+ Chip SigmaTel STAC9205

Also, does the external microphone work for you? For me only the embedded microphone works.

---

### Post by bimbo on 2007-09-07
/etc/default/acpi-support should exist on Ubuntu machines by default. As for automatically unloading when it is being used that may or may not work, I won't bother to try since it works for me thru suspend without any issues.

I have no idea if the external mic works as I don't have one.

---

### Post by geppz on 2007-09-07
Ow, previously you said /etc/acpi/acpi-support ! :-) Thanks it works now by adding the module in /etc/default/acpi-support as you say, BUT as I suspected, all sound applications must be off for the module unloading-reloading to work so since at least kmix is always running, the trick doesn't work out of the box. I would need to go with kmix disabled by default or remember to kill it before suspending. Same for amarok or other players which might be running.

Bad luck for external mic, I was really curious.

Thanks

---

