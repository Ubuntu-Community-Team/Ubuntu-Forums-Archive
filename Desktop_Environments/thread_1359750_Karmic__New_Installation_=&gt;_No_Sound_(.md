---
title: "Karmic : New Installation =&gt; No Sound :("
date: 2009-12-20
forum: Desktop Environments
---

### Post by MaximeG on 2009-12-20
Hello,



I installed Karmic a couple days ago and even if the sound was working in the beginning, this is not the case anymore. It happened after a Kernel update I guess.


I followed a blog to handle the usual sound issues, here is the result :


**Code:**

maximeg@DreamTheater:~$ lspci | grep -i "[aA]udio"
04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
0a:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)


My sound cards are there :


**Code:**

maximeg@DreamTheater:~$ aplay -l
aplay: device_list:223: no soundcards found...


As well as : 


**Code:**

maximeg@DreamTheater:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).


Yet : 


**Code:**

maximeg@DreamTheater:~$ sudo service alsa-utils restart
 * Shutting down ALSA...                                                                              [ OK ]
 * Setting up ALSA...                                                                                 [ OK ]


But when you have a look at available modules : 

**Code:**

maximeg@DreamTheater:~$ modprobe -l
video/nvidia.ko
initrd/vesafb.ko
misc/vboxnetadp.ko
misc/vboxdrv.ko
misc/vboxnetflt.ko


No snd-* :(



I tried as suggested in the blog the re-installation of alsa => gave nothing.
I also tried to reinstall "manually" the modules through module-assistant and there I had a small result : 


**Code:**

maximeg@DreamTheater:~$ modprobe -l
updates/alsa/acore/snd-hwdep.ko
updates/alsa/acore/snd-timer.ko
updates/alsa/acore/snd-page-alloc.ko
updates/alsa/acore/snd.ko
updates/alsa/acore/seq/snd-seq-virmidi.ko
updates/alsa/acore/seq/snd-seq.ko
updates/alsa/acore/seq/snd-seq-midi-event.ko
updates/alsa/acore/seq/snd-seq-device.ko
updates/alsa/acore/seq/snd-seq-midi.ko
updates/alsa/acore/seq/oss/snd-seq-oss.ko
updates/alsa/acore/seq/snd-seq-midi-emul.ko
updates/alsa/acore/snd-pcm.ko
updates/alsa/acore/oss/snd-pcm-oss.ko
updates/alsa/acore/oss/snd-mixer-oss.ko
updates/alsa/acore/snd-rawmidi.ko
updates/alsa/synth/snd-util-mem.ko
updates/alsa/synth/emux/snd-emux-synth.ko
updates/alsa/pci/ac97/snd-ac97-codec.ko
updates/alsa/pci/emu10k1/snd-emu10k1.ko
updates/alsa/pci/emu10k1/snd-emu10k1-synth.ko
updates/alsa/misc/ac97_bus.ko
video/nvidia.ko
initrd/vesafb.ko
misc/vboxnetadp.ko
misc/vboxdrv.ko
misc/vboxnetflt.ko




But now I'm lost (looks like I have the wrong version or something) : 


**Code:**

maximeg@DreamTheater:~$ sudo modprobe snd-emu10k1
FATAL: Error inserting snd (/lib/modules/2.6.31-17-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_util_mem (/lib/modules/2.6.31-17-generic/updates/alsa/synth/snd-util-mem.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.31-17-generic/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.31-17-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.31-17-generic/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31-17-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.31-17-generic/updates/alsa/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.31-17-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.31-17-generic/updates/alsa/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.31-17-generic/updates/alsa/pci/emu10k1/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And dmesg :


**Code:**

[ 4478.526587] snd: Unknown symbol unregister_sound_special
[ 4478.526855] snd: Unknown symbol register_sound_special_device
[ 4478.527820] snd: Unknown symbol sound_class
[ 4478.528297] snd_hwdep: Unknown symbol snd_info_register
[ 4478.528396] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 4478.528492] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[ 4478.528589] snd_hwdep: Unknown symbol snd_info_free_entry
[ 4478.528703] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 4478.528806] snd_hwdep: Unknown symbol snd_verbose_printk
[ 4478.528902] snd_hwdep: Unknown symbol snd_register_oss_device
[ 4478.529006] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 4478.529103] snd_hwdep: Unknown symbol snd_card_file_add
[ 4478.529220] snd_hwdep: Unknown symbol snd_iprintf
[ 4478.529327] snd_hwdep: Unknown symbol snd_major
[ 4478.529466] snd_hwdep: Unknown symbol snd_unregister_device
[ 4478.529572] snd_hwdep: Unknown symbol snd_device_new
[ 4478.529710] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 4478.529836] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 4478.529943] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 4478.530053] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[ 4478.530158] snd_hwdep: Unknown symbol snd_card_file_remove
[ 4478.530257] snd_hwdep: Unknown symbol snd_register_device_for_dev


Here we are. The only exotic thing I've done is to install (cleanly) the latest nVidia drivers (190.42), this was done flawlessly. Otherwise, all other updates have been done through the official update tool.



Even if I can drive myself through some other distributions, I'm a beginner with Ubuntu (and Debian in general) therefore I'm completely lost. So, if someone would have an idea or clue, that would make my day :)


Thanks a lot in advance !
Maxime

---

### Post by dino99 on 2009-12-20
what google says about "x-fi+karmic" ?

look at Applications --> sound --> sound control : unlock output sound

Is pulseaudio installed ?

Is Creative have Linux driver ?

---

### Post by dino99 on 2009-12-20
maybe this can help:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)   :P

---

### Post by MaximeG on 2009-12-20
Hi,

Thanks for the link, I'll have a look at it.

For the other questions : yes to all.
Actually it was working before a reboot after a kernel update.

Don't know why and how to fix it :/

Regards,
Maxime

---

