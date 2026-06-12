---
title: "Backup and Ext4 questions"
date: 2009-04-28
forum: General Help
---

### Post by Uzi304 on 2009-04-28
I'd like to use Jaunty on Ext4 because I've heard from many people that its much quicker on it. The thing is that I've only heard from people with 64 bit processors so will I be able to use Jaunty on Ext4 with a 32 bit? Are there any downsides to using Ext4? To change my drive to Ext4 all I do is run the Gparted Live CD and just change the Ext3 to Ext4 right? I'd obviously have to do a fresh install so my question about backing up is that is there a better way to do it instead of just copying and pasting files to another drive? Also what would I have to backup to make the fresh install exactly like the one I'm running right now? A lot of questions, I know but any help will be appreciated.

---

### Post by lovinglinux on 2009-04-28
> **Uzi304 said:**
> I'd like to use Jaunty on Ext4 because I've heard from many people that its much quicker on it. The thing is that I've only heard from people with 64 bit processors so will I be able to use Jaunty on Ext4 with a 32 bit? 

Yes. You need to select manual partitioning to use ext4 during the install process, since the assisted process uses ext3 be default (I guess).

> **Uzi304 said:**
> Are there any downsides to using Ext4?

[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

> **Uzi304 said:**
> To change my drive to Ext4 all I do is run the Gparted Live CD and just change the Ext3 to Ext4 right?

You don't have to run Gparted, just run the installation from the CD, delete the existing partitions and create new ones with ext4 and proceed with installation. If you have a separate partition for home, then you could format the system partition as ext4 and keep the home as ext3 without formatting, just mounting it. This will preserve all the contents. Backup is still recommended anyway.

> **Uzi304 said:**
> I'd obviously have to do a fresh install so my question about backing up is that is there a better way to do it instead of just copying and pasting files to another drive?

You could use a tool like rsync, but what it does is essentially copying the content to another drive. 

> **Uzi304 said:**
> Also what would I have to backup to make the fresh install exactly like the one I'm running right now? A lot of questions, I know but any help will be appreciated.

First, backup your /home. Most of your personal configurations are stored there.

Then follow this to create a list of installed applications and restore them after the fresh install:

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

Then restore your home directory.

You will loose some configurations that are stored in other folders like /etc, but if you didn't tweak the system a lot, probably it won't be necessary to redo too many things.

---

### Post by Uzi304 on 2009-04-28
Wow thanks a lot! I won't have time to do all this until tomorrow but hopefully I can do all this problem-free. But if you could clear something up, there is also an extended partition and a linux-swap. Do I need to delete those too or just the ext3 partition?

---

### Post by lovinglinux on 2009-04-28
> **Uzi304 said:**
> Wow thanks a lot! I won't have time to do all this until tomorrow but hopefully I can do all this problem-free. But if you could clear something up, there is also an extended partition and a linux-swap. Do I need to delete those too or just the ext3 partition?

Linux swap is where the system copy files when there is no more available RAM memory. You can keep it or create e new one if you want to change its size. 

The extended partition is usually used when you need more then 4 partitions. You can't create more then 4 primary partitions, but you can create an extended one. It basically works like a single partition, containing sub-partitions. So you have to check which partitions are inside the extended, because if you format it, you will wipe the sub-partitions inside it.

I personally don't like extended partitions. I had a lot of problems with them on my Windows time. If you can create a primary, then I recommend to do it instead of creating an extended. It is easier to manage them.

I forgot to mention that you need to copy the hidden files when backing up the home partition, to preserve your personal configurations.

---

### Post by Uzi304 on 2009-04-28
Well my extended partition contains my linux-swap partition so I think I will just leave that alone. The ext4 will be the primary partition. Also when I copy the entire home folder, won't it copy all the hidden files too or do I have to copy them separately? To use ext4 it also said I had to do something with GRUB, can you explain what I have to do with that?

---

### Post by Sef on 2009-04-28
> To use ext4 it also said I had to do something with GRUB, can you explain what I have to do with that?

With Ubuntu, GRUB can read ext4, so nothing else to do.

---

### Post by lovinglinux on 2009-04-28
> **Uzi304 said:**
> Well my extended partition contains my linux-swap partition so I think I will just leave that alone.

If it only contains the swap, then you can delete it without worries and create a new swap. It doesn't contain important data.

> **Uzi304 said:**
> The ext4 will be the primary partition. Also when I copy the entire home folder, won't it copy all the hidden files too or do I have to copy them separately? 

Yes, it copies. I just wanted to make sure you know the configuration files are there.

Don't forget to [create a separate partition for the home](http://www.psychocats.net/ubuntu/separatehome) directory in your new installation. It will make easier for you to make another fresh install in the future, without losing your configuration files and without formatting the home again.

---

### Post by Uzi304 on 2009-04-28
Alright. Thanks for all the help, lovinglinux, I really appreciate it. Thank you too, Sef. I'll post how everything went tomorrow if anyone's insterested

---

### Post by lovinglinux on 2009-04-28
> **Uzi304 said:**
> Alright. Thanks for all the help, lovinglinux, I really appreciate it. Thank you too, Sef. I'll post how everything went tomorrow if anyone's insterested

You are welcome. Good luck.

---

### Post by whoop on 2009-04-29
You can also convert your ext3 partitions to ext4 using this howto:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by Uzi304 on 2009-04-29
> **whoop said:**
> You can also convert your ext3 partitions to ext4 using this howto:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

Thank you but programs that were installed on the ext3 system will not be affected so I think for me it'll just be better just to backup my files and do a fresh install.

---

### Post by whoop on 2009-04-29
> **Uzi304 said:**
> Thank you but programs that were installed on the ext3 system will not be affected so I think for me it'll just be better just to backup my files and do a fresh install.

All files will eventually be replaced by updates and upgrades, the new kernel will support an on line defragger. So the problem will solve itself. But to each his own, I just prefer doing upgrades over fresh installs. My current installs are a couple of years old without doing fresh installs. It doesn't slow the system down as often happens with other OS upgrades.

---

### Post by Uzi304 on 2009-04-29
Oooh I wish I had read your post sooner, whoop. Thank you for trying to help but my ignorance stopped me from making it easier for me. Anyways I successfully am able to use the ext4 filesystem and it really is very snappy as others have claimed. I'm glad I made the switch. It took me a couple hours but I got it done. Again, thanks to everyone who helped in this thread. :D

---

