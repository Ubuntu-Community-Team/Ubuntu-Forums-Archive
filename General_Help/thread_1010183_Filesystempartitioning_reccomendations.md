---
title: "Filesystem/partitioning reccomendations?"
date: 2008-12-13
forum: General Help
---

### Post by jmite on 2008-12-13
On a 320GB Laptop, I'm considering paritioning my disk like this:

20GB Windows Vista NTFS (Mostly just to use iTunes or any other programs that Wine doesn't like)

40GB Ubuntu System Parition, ext3 (this is my main OS)

20GB ext3 openSUSE System partition (or any other OS, basically a parition to experiment with distros

11GB ext3 Gentoo System partition (Basically, I'm using this only for cinelerra and video editing, I'll set up a minimalist DE and disable unnecesarry services so that it will be as fast as possible)

4GB Swap

230GB JFS /home partition


I have a few questions about this setup:
Is it possible to have my home folder shared between all the linux OSes?

What are the pros and cons of XFS, JFS, EXT3 for the /home folder? Which is the safest? Which is the fastest?

Is 40GB big enough for the Ubuntu partition, if that's my main system folder?

Is 20GB big enough for vista? Seeing as I'm using it the least, I'd like to give it as little space as possible.

Will having a large Swap slow down my system? I wanted 4GB so that if I suspended to disk, the entire contents of the 4GB of ram would fit on the disk.

Does anyone see immediate problems with this setup?

Thanks!

---

### Post by nielz on 2008-12-13
I would most certainly advise NOT to use XFS because it's guarantueed to corrupt any opened files when your power fails or you have to do a hard reboot because of e.g. a lockup. You may think this won't ever happen, but it will and you will hate yourself for using XFS :)

JFS on the other hand is (on average) faster than both ext3 and XFS and will not eat your files, making it a good choice. Google has a lot of benchmarks comparing the filesystems you mention.

Also, if you want to experiment with distro's and run windows, why not use virtualization (virtualbox or vmware). I would look into wether your specific type of virtualization supports whatever you'd want to do with itunes though. 

Finally, yes, 40gb is plenty for an ubuntu system. Also a big swap partition won't make your system slow. On moderns computers with lots of memory swap is mostly unused anyway.

Hope this helped :)

---

