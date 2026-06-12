---
title: "module with unwanted parameter loading"
date: 2009-02-18
forum: General Help
---

### Post by gdoteof on 2009-02-18
```
gdot@gdot-ubuntu:~$ modprobe -c | grep snd-hda-intel
options snd-hda-intel model=laptop
options snd-hda-intel model=3stack-6ch-dig

```

I want to NOT load the snd-hda-intel model=laptop.

I have added the 2nd line w/ 3stack-6ch-dig to my /etc/modprobe.d/alsa-base

```
cat /sys/module/snd_hda_intel/parameters/model
laptop,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>

```

I changed that file, to say 3stack-6ch-dig,NULL, etc.. (as root, i had to chmod it to even be able to).  when i rebooted the file was changed back

---

