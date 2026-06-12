---
title: "Ubuntu 14.04 NVIDIA Driver Refusal"
date: 2014-05-12
forum: Desktop Environments
---

### Post by MnFork on 2014-05-12
I can not seem to get Ubuntu to use my Nvidia card after upgrading from 13.10 to 14.04.

I'm using an Nvidia GeForce GT750M (lspci output):
```
04:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
```

I have tried:
[LIST]
[*]nvidia-current (3.04 at time of writing)
[*]nvidia-319
[*]nvidia-319-updates
[*]nvidia-331 from repos (through apt-get)
[*]nvidia-331 from the Nvidia script
[*]nvidia-331 from Additional Drivers
[*]nvidia-331-updates from additional drivers
[*]combinations of bumblebee and prime with the above
[/LIST]

Any thing that I install fails to load a module (as determined by lsmod | grep -i nvidia) and fails to provide nvidia-xconfig.

I have tried reinstalling all packages several times.

I have been careful to purge nvidia* between versions.

I have removed nouveau and blacklisted it in /etc/modprobe.d/blacklist.conf

After I install nvidia I only have nvidia-detector, which always returns none, and nvidia-settings, which displays the behavior found here: [http://http://askubuntu.com/questions/455717/ubuntu-14-04-nvidia-settings-is-empty]("http://http://askubuntu.com/questions/455717/ubuntu-14-04-nvidia-settings-is-empty")

I have no idea what else to do or search on this one.

---

### Post by Onamission on 2014-05-13
I am having a very similar problem with a NVIDIA Geforce 7000

I found multiple threads with a similar issue but no real solution:
[http://ubuntuforums.org/showthread.php?t=2217923](http://ubuntuforums.org/showthread.php?t=2217923)
[http://ubuntuforums.org/showthread.php?t=2210995](http://ubuntuforums.org/showthread.php?t=2210995)

I even tried to follow this guide with no avail.
[http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu1404/](http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu1404/)

Every time it fails to load as a module.  Im not sure what else to try.

---

### Post by Chris_Salzberg on 2014-07-08
Same issue here with Quadro K2000M on a Lenovo W530. I've tried everything and nothing seems to work. Used to work fine in 13.10 with discrete mode.

If anyone has a solution to this please share!

---

### Post by Chris_Salzberg on 2014-07-08
OK I managed to solve this for my setup. This may or may not work for you.

First, purge whatever nvidia drivers you currently have with sudo apt-get purge nvidia-*.

Then add the xorg-edgers ppa:

> 
sudo add-apt-repository ppa:xorg-edgers/ppa


Then install the latest version of nvidia:

> 
sudo apt-get install nvidia-337


I then rebooted with discrete mode and everything works.

---

### Post by Chris_Salzberg on 2014-07-08
OK I managed to solve this for my setup. This may or may not work for you.

First, purge whatever nvidia drivers you currently have with ```
sudo apt-get purge nvidia-*
```.

Then add the xorg-edgers ppa:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

Then install the latest version of nvidia:

```
sudo apt-get install nvidia-337
```

I then rebooted with discrete mode and everything works.

---

