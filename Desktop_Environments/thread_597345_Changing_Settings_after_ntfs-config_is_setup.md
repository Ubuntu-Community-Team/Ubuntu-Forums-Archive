---
title: "Changing Settings after ntfs-config is setup"
date: 2007-10-30
forum: Desktop Environments
---

### Post by mainertoo on 2007-10-30
I was able to successfully setup my ntfs-config and tell the application which NTFS partitions I wanted to mount and what to name on of them which had no name. Once this was complete, the 2 partitions that are being mounted show up as icons on the desktop. 

The issue I am having is that I want to change the way in which the "automount" is working and I cannot figure out where to find the settings I can edit for ntfs-config. Running the application again does not give any configuration options that can be changed, it only allows you to choose whether or not to read internal and/or external drives.

Is there a file I can find to edit the ntfs-config settings or even a place i can reset the settings so I can run the "setup" again? I have looked at the fstab file but this didn't seem to me to be product of running ntfs-config. But I could be very wrong on that. 

Thanks in advance for the help.

---

### Post by mainertoo on 2007-11-03
Just a shameless bump hoping someone has either dealt with this or knows how to reconfigure ntfs-config, because I am kinda lost trying.

---

### Post by asimon on 2007-11-03
I never used ntfs-config, but /etc/fstab should be the right file.

If the GUI tool doesn't give you access to all options you can always edit /etc/fstab with any file editor.

In the following example line from /etc/fstab (you want the lines with nfts-3g as file system type)
```
/dev/mapper/isw_bgjcdcfheh_volume01 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 1
```
the comma seperated options list is "defaults,locale=en_US.utf8". To change the automount behaviour just add noauto at the end of it, i.e.
```
/dev/mapper/isw_bgjcdcfheh_volume01 /media/windows ntfs-3g defaults,locale=en_US.utf8,noauto 0 1
```
auto (which is part of defaults), means that the partition will get mounted by 'mount -a', in practice this means that it will be automatically mounted during boot, noauto means it must be mounted manually.

---

