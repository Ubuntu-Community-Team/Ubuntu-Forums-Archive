---
title: "modprobe"
date: 2005-09-05
forum: Desktop Environments
---

### Post by one_ro on 2005-09-05
Hi guys,

After recompiling the alsa drivers, as well as compiling the alsa-lib and alsa-utils packages, I now want to issue the command:
[COLOR=Red]sudo modprobe snd-intel8x0[/COLOR]
which gives me errors like:
[COLOR=Blue]WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.10-5-386/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_intel8x0
[/COLOR]

Could anybody point me in the right direction?
TIA,
Adrian

---

### Post by mlomker on 2005-09-05
What is **dmesg** telling you?  It sounds like they didn't compile properly.  Did you get errors during  the compile?  

I have the same sound card in my laptop and it worked without recompiling.

---

### Post by one_ro on 2005-09-06
[QUOTE=mlomker]What is **dmesg** telling you?  It sounds like they didn't compile properly.  Did you get errors during  the compile?  

I have the same sound card in my laptop and it worked without recompiling.[/QUOTE]

Oh, I had no error compiling the driver. But nevertheless, the simplest solution hit me:
[COLOR=Red]sudo apt-get update[/COLOR]
(of course, after adding the repos for KDE 3.4.2)

Now I have sound alright, it just seem a bit shifted in MPlayer but I can live with that.

Thanks for everything.

---

