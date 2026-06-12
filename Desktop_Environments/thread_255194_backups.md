---
title: "backups"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Russty of Oz on 2006-09-11
Hi,

I have noticed some things in Synaptic with the names **backup manager** and **backuppc**, I was wondering if these are any good for doing a full backup of my Ubuntu OS so that I can install it, as-it-is, on my other computer and also to reinstall should this one crash?

If there is any other way of doing a backup, I would be very pleased to hear about it.  Someone did mention **sudo rsync -aS** in the the terminal but that doesn't seem to work, I just get error (code 1).

Russty.

---

### Post by ajgreeny on 2006-09-11
Have a look at partimage, which will make an image of your whole partition which can then be transferred to another machine, though you may need to make changes to some config files as the drive letters may be different and there will probably be different hardware.  Worth looking at seriously, however.

---

### Post by lukew on 2006-09-11
Wrong parameters. RSYNC Rocks... well quick, much quicker than robotcopy!!! If not copying files my rysnc compares over 55000 files in about a second.

rsync -vurt --progress --delete /home/luke/data/ /media/lacie/backup

I hope this helps.

Rsync gets a bit confused when copying onto vfat, you probably want to copy onto ext3 other wise it will just copy the whole lot.

If it has to be vfat then cp -u works pretty good.


Luke

---

### Post by Russty of Oz on 2006-09-11
Hmmm, I will check out partimage.

Now, lukew, you are obviously far more advanced with this sort of thing than me, so I am not sure what all that means.  Could you explain a little bit more what I need to do? I don't know what the vfat and cp -u is all about.  What do I need to put in the terminal to get rsync to work?

Russty

---

### Post by rbmorse on 2006-09-11
Don't forget kdar. It's sort of like rsync with lipstick. Has a nice GUI and it's comes with the base package.

---

### Post by aysiu on 2006-09-11
Actually, the GUI frontend for *rsync* is *grsync*.

For a Ubuntu-specific PartImage tutorial, go here:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Russty of Oz on 2006-09-12
> **aysiu said:**
> Actually, the GUI frontend for *rsync* is *grsync*.

For a Ubuntu-specific PartImage tutorial, go here:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Thanks, that is just what I wanted!:D 

I will have to do that as soon as I can get gnome working again, there isn't much point saving my system when it won't work properly.

Russty.

---

