---
title: "VegaStrike extremely slow on 5700"
date: 2005-07-01
forum: Gaming &amp; Leisure
---

### Post by Prudentissimus on 2005-07-01
Is FX 5700 supported on Ubuntu?

VegaStrike game is very very slow on it...

How can I fix it

---

### Post by MappyH on 2005-07-01
I have 5700 and run games ok, make sure you have nvidia drivers installed.

have a look here [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Prudentissimus on 2005-07-01
[QUOTE=MappyH]I have 5700 and run games ok, make sure you have nvidia drivers installed.

have a look here [http://ubuntuguide.org](http://ubuntuguide.org)[/QUOTE]
 The problem is that I don't.

I don't have internet access, therefore I cannot just use APT GET.

Though I have the *.run file (Linux drivers) directly from NVidia.

The installation requires KERNEL-SOURCE-TREE. I'm not sure if I have it, and if I do, where should I point the PATH of NVIDIA INSTALLATION to to find KERNEL-SOURCE...

---

### Post by MappyH on 2005-07-01
Have a look here [http://www.ubuntuforums.org/showthread.php?t=42763](http://www.ubuntuforums.org/showthread.php?t=42763)  :smile:

---

### Post by ubuntu_demon on 2005-07-01
you should download the nvidia packages mentioned in ubuntuguide using [http://packages.ubuntu.com](http://packages.ubuntu.com)

and then just install them with
$sudo dpkg -i packagename

---

### Post by Prudentissimus on 2005-07-02
[QUOTE=demon666_nl]you should download the nvidia packages mentioned in ubuntuguide using [http://packages.ubuntu.com](http://packages.ubuntu.com)

and then just install them with
$sudo dpkg -i packagename[/QUOTE]
 I fixed it.


sudo nvidia-glx-config enable


20k GLX / 5 seconds

---

