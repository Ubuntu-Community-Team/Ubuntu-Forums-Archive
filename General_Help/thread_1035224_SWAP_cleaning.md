---
title: "SWAP cleaning ?"
date: 2009-01-09
forum: General Help
---

### Post by iKonaK on 2009-01-09
Is there any way that I could clean the swap whit out rebooting ?
Also is there any elegant way to dump RAM in swap, I run GIMP and create new large high rez files until my my RAM is forced to swap and then i kill the gimp's PID :) and i get free RAM, but i'm sure is a simpler elegant way to do this...

---

### Post by andrewc6l on 2009-01-09
I'm not sure what your intent is. You can list the swap files with:

# swapon -s

That will show you which partitions are being used as swap. Once you know what those are, you can turn swap off using swapoff -v /dev/hda3 (or whatever swapon -s shows you). You can turn swap back on by using swapon -v /dev/hda3 (or just swapon -a -e to turn it on the way it's done by the boot process).

---

### Post by iKonaK on 2009-01-10
Thanks, that kind of did the trick for the swap but i would also like to know how to dump unnecessary ram to swap, i guess i'll just do the gimp trick but is not that fast and elegant for that matter.

---

### Post by andrewc6l on 2009-01-12
Here's an article that describes Linux swap space:
[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

From that article:

The Linux 2.6 kernel added a new kernel parameter called swappiness to let administrators tweak the way Linux swaps. It is a number from 0 to 100. In essence, higher values lead to more pages being swapped, and lower values lead to more applications being kept in memory, even if they are idle. Kernel maintainer Andrew Morton has said that he runs his desktop machines with a swappiness of 100, stating that "My point is that decreasing the tendency of the kernel to swap stuff out is wrong. You really don't want hundreds of megabytes of BloatyApp's untouched memory floating about in the machine. Get it out on the disk, use the memory for something useful."

One downside to Morton's idea is that if memory is swapped out too quickly then application response time drops, because when the application's window is clicked the system has to swap the application back into memory, which will make it feel slow.

The default value for swappiness is 60. You can alter it temporarily (until you next reboot) by typing as root:

echo 50 > /proc/sys/vm/swappiness

If you want to alter it permanently then you need to change the vm.swappiness parameter in the /etc/sysctl.conf file.

---

