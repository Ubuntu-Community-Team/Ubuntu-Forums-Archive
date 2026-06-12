---
title: "failed to load nvidia kernel module"
date: 2010-08-08
forum: Desktop Environments
---

### Post by tom1983 on 2010-08-08
hi all,

my laptop broke beyond repair recently so im stuck on a 6 year old hp pavilion zv5000 given to me by a friend and i thought I may as well give linux a go, i have been meaning to for years.

Ive installed xubuntu 10.04 as i heard it is less resource intensive than normal ubuntu but have been unable to configure the nvidia graphics card. I used the hardware drivers program which installed the nvidia accelerated graphics driver 96 (which was the recommended version) and then ran sudo nvidia-xconfig as instructed and got 

```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

```

which I presume means it worked correctly, but whenever I try to boot I get a message saying "failed to load nvidia kernel module", at which point I either have to restore the generic configuration or just start the session in low graphics mode.

i have googled the problem and in a lot of peoples cases it seems to be linked to upgrading from a previous version whilst mine was a fresh install. i tried sudo modprode and it says the nvidia module isnt present. i tried installing the packages in synaptic which mentioned nvidia kernel modules but still no luck.

if anyone could help I would be really greatful, everything seems to be running fine except this :(

thanks in advance

---

### Post by tom1983 on 2010-08-08
fixed.

I realised I'd installled the drivers before installing all the system updates so i tried uninstalling them again and reinstalling and its working.

Thanks anyway

---

