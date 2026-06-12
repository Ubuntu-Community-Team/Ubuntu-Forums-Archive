---
title: "making partitions in ubuntu installed HDD"
date: 2009-02-11
forum: General Help
---

### Post by keronbn on 2009-02-11
hi,
        I am a newbie.I was trying to install Ubuntu on my HDD.I tried at first to make an install, after booting through installation CD and make partitions.But it seems like ubuntu takes up all the HDD and does not provides an option for making a second partition(I am not sure about manual steps).
      After installation I tried resize partition using Gpart and shrinked the HDD image from right to left to resize it.But Gpart showed operation in progress,but nothing really happened.I waited for 1 hour,then cancelled it.On rebooting ubuntu was not booting up.
       I tried another bootCD for creating linux partitions first and then tried installing Ubuntu.Then it appeared like ubuntu selects the last created partition for installation.or was it random?
       I want to make 2 partitions in 80Gb HDD with  50 Gb for installing Ubuntu and a 30Gb for saving files.After making the second partition I want to change my home directory to it to prevent data loss.
please some one help me with
[LIST]
[*]making a partition during installation of ubuntu.
[*]installing ubuntu in desired partition I want to install
[*]change
[/LIST]the home directory from installed partition to another partition

---

### Post by kanikilu on 2009-02-11
Here is a guide on how to manually partition during the install so that /home is in it's own partition:

[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install](http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install)

And here is a guide on how to do it if you already have Ubuntu installed on the entire disk:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you are doing a new install and can wipe the entire disk, I'd say go with the first guide above, it's much simpler than doing it after installing.

---

### Post by keronbn on 2009-02-11
Thank you so much.I guess it is the answer I need.One more question.How much space I should allocate for installing Ubuntu and if I need to run a virtual machine with WindowsXP or Vista.Will the space for that installation will be taken from the partition in which Ubuntu is installed?

---

### Post by kanikilu on 2009-02-12
My "/" partition is taking less than 7GB right now. I would think anything larger than 15GB would be overkill for the root partition...at least in my case.

As for virtual machines, I think you can put them anywhere you want. I use virtual box which puts the vm's in ~/.VirtualBox/ (in my home directory) by default, so I personally set the /home partition to take up the rest of my available disk space (after allocating room for / and swap).

---

