---
title: "Starting Hotplug Subsystem  = Locks up."
date: 2006-04-15
forum: Desktop Environments
---

### Post by trixx on 2006-04-15
Ok, so I'm using a HP Pavilion a1030n

P4 Processor.

i've tried Kubuntu, and Ubuntu, Ubuntu first. I figure, maybe Kubuntu WONT lock up on Starting Hotplug Subsystem. no such luck, my PC locks at starting hotplug subsystem. i've left it on for more than an hour, to see if its just slow. no, theres a problem with it... any help?

---

### Post by abdulhaq on 2006-04-16
Is your sound card based on an Intel HD Audio card?

---

### Post by trixx on 2006-04-16
yep. how can I fix?

---

### Post by abdulhaq on 2006-04-16
What I did was to get onto the machine via a different (e.g. live) distribution and rename the snd-intel-hda module to something else so that ubuntu couldn't try and load it, i.e. 

rename /lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-intel.ko to
something else

and all should be well.

I now have sound working by using the 2.6.15 kernel from the upcoming Dapper release.

abdulhaq

---

### Post by trixx on 2006-04-17
i dont know how to do that though :( i have NEVER used linux before. I have a Gentoo livecd, but it loads to something kind of like Command prompt... can I do  it from there? If so, how? What code?

---

### Post by abdulhaq on 2006-04-17
Well you should be able to do it from the gentoo 'command prompt'. 

1. First you need to find where Gentoo is mounting your disk partitions. Try:

cd /
ls

(BTW ls = dir)

and there should be something like a /mnt or a /media directory which is where Gentoo mounts your local partitions. Under that directory there should be one directory for each drive e.g. /mnt/hda1 for Windows C: drive and /mnt/hda2 or /mnt/hdb1 for the second partition. It might also be called /mnt/win_c or something like that. In one of those directories is where you will find the root of the Ubuntu partition so you will see (using ls)
directories called /etc and /lib and /bin plus others.

So go to the lib/modules directory

```

cd /mnt/hda1
cd lib/modules

```

then cd to the appropriate directory (e.g. /2.6.12-9-386)

```

cd 2.6.12-9-386

```

and then

```

cd /kernel/sound/pci/hda/

```

You should then be in a directory called

/mnt/hda1/lib/modules/2.6.12-9-386/kernel/sound/pci/hda

or something like that. Then rename the offending file:

```

mv snd-hda-intel.ko snd-hda-intel.ko.orig

```
at which point you might need to be logged on as root if it says that you dont have sufficient privileges.

You can then reboot into Ubuntu.

Hope that makes some sense
abdulhaq

---

### Post by trixx on 2006-04-17
ok, thanks, i'll try that now.

---

