---
title: "Question about root and home partitions"
date: 2009-05-30
forum: General Help
---

### Post by puscifer919 on 2009-05-30
Hey all, I have a few quick questions regarding the way a Linux OS installation works with my /home partition. Keep in mind that I have 3 partitions; /, /home, and my swap partition.

1) If I were to format my / partition and reinstall Ubuntu with my existing /home partition intact, what could I expect upon completion of the new install? My pics, music, and documents would be there, but what about programs, settings, etc?

2) What if I were to install Fedora instead of Ubuntu? Would that change the answer to my first question at all?

3) I'm using 9.04 now and I'd like to go back to 8.10. Would this method be the simplest, most effective way of doing this? (In case anyone is wondering, I'm experiencing nothing but bugs in 9.04, from audio and video issues, to programs crashing, you name it.)

Thanks a lot, guys!

---

### Post by merlinus on 2009-05-30
You certainly can install a new (or older) version in the partition where / resides.  Select /home to be used, and its mountpoint, but do not format it, and your data and most program settings will be retained.

If, however, you go back to an older version, then some settings may not work, e.g. 8.10 has OpenOffice 2.4, not 3.

---

### Post by tuxxy on 2009-05-30
1) All your personal files in /home would be intact, just remember to assign your current /home partition the mount point /home at installation of new Ubuntu.

2) It should work but I would advise against using same /home for different distributions

3) Install 8.10 as normal and select manual partitioning at the partition stage of the installation. Then assign you filesystem to mount point / and /home to /home

---

### Post by puscifer919 on 2009-05-30
Thanks for the quick answers! I can't wait to get back to Intrepid! :D

---

### Post by mocoloco on 2009-05-30
In case you're not aware, all of you setting for applications are in hidden folders in your home folder. So Installing another version of your distro or a different distro will usually work fine provided the apps are either the same versions or know what to do with the config files of other versions (which may or may not change).

---

### Post by blueridgedog on 2009-05-30
> **puscifer919 said:**
> Thanks for the quick answers! I can't wait to get back to Intrepid! :D

I guess I am a late adopter as I will probably stay on intrepid until I have some reason to do a clean install, but at this point will probably wait until karmic.

---

### Post by puscifer919 on 2009-05-30
> **mocoloco said:**
> In case you're not aware, all of you setting for applications are in hidden folders in your home folder. So Installing another version of your distro or a different distro will usually work fine provided the apps are either the same versions or know what to do with the config files of other versions (which may or may not change).
I was not aware. Thanks!

> **blueridgedog said:**
> I guess I am a late adopter as I will probably stay on intrepid until I have some reason to do a clean install, but at this point will probably wait until karmic.
I like to jump on things as soon as they are available. Probably not always the best idea. I actually installed 9.04 Beta several months ago and had to be rescued by the members of these very forums when my Xorg configuration was damaged due to an nVidia driver related conflict of some sort. :(

---

### Post by lovinglinux on 2009-05-30
To install the same programs you have right now after re-installing, follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

Since your /home will be preserved, then most programs settings will also be preserved as they are now, except when they have versions incompatibilities, as already mentioned.

---

### Post by puscifer919 on 2009-05-30
Thanks for the tip, **lovinglinux**. I'll definitely make use of it.

---

### Post by puscifer919 on 2009-05-30
Ahhh... it's just like I remember it. Exactly the same, except it works right. =P

Thanks again guys.

---

### Post by lovinglinux on 2009-05-30
> **puscifer919 said:**
> Ahhh... it's just like I remember it. Exactly the same, except it works right. =P

Yep. Having a /home partition is really useful on these situations. When I was using Hardy I tried Intrepid but didn't liked it, so I installed Hardy again and everything was just like before. 8)

---

### Post by blueridgedog on 2009-05-30
> **puscifer919 said:**
> Ahhh... it's just like I remember it. Exactly the same, except it works right. =P


I know the feeling.  Right now with 8.10, everything I have works great, I have the latest open office and life is good.

---

### Post by dcstar on 2009-05-30
> **lovinglinux said:**
> To install the same programs you have right now after re-installing, follow this:
.........

You don't need to do any command line stuff at all.

Simply use Synaptic's "Save Markings" on the old system and then do a "Read Markings" on the new system to reinstall all the packages.

---

### Post by lovinglinux on 2009-05-31
> **dcstar said:**
> You don't need to do any command line stuff at all.

Simply use Synaptic's "Save Markings" on the old system and then do a "Read Markings" on the new system to reinstall all the packages.

You are not the first one who says that, but it doesn't work as you think. When you save the markings, the generated saved file will have nothing inside and 0 bytes, unless the packages you want weren't previously installed and you mark them to be installed first. So, that defeats the purpose of saving a list of applications you have already installed.

---

### Post by tantric rex on 2009-10-04
> **lovinglinux said:**
> You are not the first one who says that, but it doesn't work as you think. When you save the markings, the generated saved file will have nothing inside and 0 bytes, unless the packages you want weren't previously installed and you mark them to be installed first. So, that defeats the purpose of saving a list of applications you have already installed.


ummm...i'm new so i may be wrong, but it'll prolly work if (instead of "save markings") you:

1. use "save markings AS..."
2. in the resulting dialog box, mark the checkbox for "save full state, not only markings"


at least it did for me.

---

### Post by sopadeajo on 2009-10-04
> **tantric rex said:**
> ummm...i'm new so i may be wrong, but it'll prolly work if (instead of "save markings") you:

1. use "save markings AS..."
2. in the resulting dialog box, mark the checkbox for "save full state, not only markings"


at least it did for me.

The names of the programs kept inside the files (the generated by synaptic and the generated by the command line) are in a different order and in my case the synaptic kile is 28.2 KB and the other is 31.6 KB. A small difference of only +1.2 %, but i cannot explain it.

If i have understood well you do not need, if you do not have much own stuff on home folder; to keep this home folder since you always can recuperate the downloaded programs these two ways and backup the config files on home folder to a backup device and copy them back again on installing the new (or old) version. Or am i wrong and should i have to use Gparted to create a partition for my home folder ?

---

### Post by lovinglinux on 2009-10-05
> **tantric rex said:**
> ummm...i'm new so i may be wrong, but it'll prolly work if (instead of "save markings") you:

1. use "save markings AS..."
2. in the resulting dialog box, mark the checkbox for "save full state, not only markings"


at least it did for me.

Yep, it works. Thanks a lot.

---

