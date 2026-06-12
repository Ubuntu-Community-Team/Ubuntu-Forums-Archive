---
title: "Partition"
date: 2009-05-02
forum: General Help
---

### Post by Tanner2007 on 2009-05-02
Long story short, i have a sd card that has a ext2 partition I need to delete off of it, now I still dont know much about ubuntu I mean I download programs and files and have no clue how to open nor install them thats how bad I am, do how could I access this ext2 partition and delete it off my sd card?

---

### Post by taurus on 2009-05-02
Do you want to reformat it to something else?  Install gparted and use it to delete ext2 filesystem on your thumbdrive then.  Make sure the drive is not mounted first before you attend to delete it though.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by geirha on 2009-05-02
In general, you don't want to download and install software you find on the web. Most of the programs you'll need, you'll find in the package repositories. In the cases where you need to install software that are not available from the repositories, you should try to find .deb-packages of it, either for Debian or Ubuntu. I recommend you read the chapter on Adding and removing software at [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by Tanner2007 on 2009-05-02
So .deb is usually files to install things?

also how do i un mount a drive?

---

### Post by geirha on 2009-05-02
> **Tanner2007 said:**
> So .deb is usually files to install things?

Yes, double-clicking a .deb-file will open it in gdebi, which will show you some information on what it contains and provide you an option to install it. But as I said, always look in the repositories first. You'll get automatic updates of whatever you install. If you need an app with a GUI, go to Applications -> Add/Remove, and to search for all available packages, go to System -> Administration -> Synaptic Package Manager.

> **Tanner2007 said:**
> also how do i un mount a drive?

For USB-drives, CDs and similar, right click it on the desktop or in nautilus (the file browser) and select unmount/eject. You can also unmount it from gparted. Read [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) for instructions on how to use gparted.

---

### Post by Tanner2007 on 2009-05-02
Thanks everyone, is there somewhere that can tell me how ubuntu works? like file types and what things are and etc?

---

