---
title: "Inspiron N7110 can't find /etc/modules.conf"
date: 2011-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by harrisoncohix on 2011-10-30
Running 11.10, trying to resolve audio issue [here]("http://ubuntuforums.org/showthread.php?t=1871686"). Can't find the module config file to edit, do they even have it with Oneiric? Here's what I was up to:

```
harrisoncohix@harrisoncohix-Dell-System-Inspiron-N7110:~$ sudo modprobe snd_hda_intel model=laptop-dmic
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 1: ignoring bad line starting with '^X'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 13: ignoring bad line starting with '^X'

```

Thanks!

---

### Post by ActionParsnip on 2012-05-10
I suggest you delete the files mentioned, they currently aren't doing anything as they don't have the file extension .conf which the files in that folder must have to be processed. Delete or move them to some storage / back them up so they are not in the folder.

---

