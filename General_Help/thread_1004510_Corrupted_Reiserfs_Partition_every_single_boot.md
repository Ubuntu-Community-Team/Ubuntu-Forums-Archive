---
title: "Corrupted Reiserfs Partition every single boot"
date: 2008-12-07
forum: General Help
---

### Post by AusIV4 on 2008-12-07
I'm using full disk encryption on my laptop, and I have a Reiserfs boot partition. Every time I boot, I get an error saying that the initrd cannot be found, and the system kernel panics. After a while, I figured out that this was because my filesystem was corrupt. I can run ```
sudo reiserfsck /dev/sda1 --rebuild-tree
``` from my live flash drive, and then get a successful boot, but next time I reboot, I'm back to having a corrupt system.

Any guesses as to why this would happen? It's getting really annoying to have to boot my laptop from a flash drive, run a command, then reboot.

---

### Post by taurus on 2008-12-07
Would you still get the kernel panic if you don't encrypt the whole harddrive?  Instead of encrypting the whole harddrive, what if you only encrypt your $HOME?

---

### Post by AusIV4 on 2008-12-07
> **taurus said:**
> Would you still get the kernel panic if you don't encrypt the whole harddrive?  Instead of encrypting the whole harddrive, what if you only encrypt your $HOME?

There are a few of problems with this. 

First, some of the development I'm doing requires data be outside of /home, and I'd like to keep this encrypted in the event that my laptop were stolen.

Second, I've been running full disk encryption for nearly a year. This problem started about a week after I re-installed to upgrade to Intrepid. Previously I had used an ext3 /boot partition, but I wanted to use reiserfs to avoid the routine fsck's (a lot of good that seems to be doing me).

I'm going to try migrating my /boot partition back to ext3 without doing a full re-install. I'll update when I know how it went.

---

### Post by xblong on 2008-12-07
Hans Reiser is a convicted murderer. He murdered his wife, the mother of his children.

During his trial he claimed he was innocent of the murder. But when he was convicted he led the police to his wife's body in exchange for a reduced sentence. 

He is now in San Quentin State Prison serving his sentence of fifteen years to life.

---

### Post by xblong on 2008-12-07
Hans Reiser is a convicted murderer. He murdered his wife, the mother of his children.

During his trial he claimed he was innocent of the murder. But when he was convicted he led the police to his wife's body in exchange for a reduced sentence. 

He is now in San Quentin State Prison serving his sentence of fifteen years to life.

[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

---

### Post by AusIV4 on 2008-12-08
I switched to an ext2 boot partition. I copied my data to my home directory, formatted as ext2, moved the data back, edited grub/menu.lst to point to the new UUID, ran grub and installed grub using the new file system. Seems to be working fine.

xblong: I'm aware of Hans Reiser's history, but it has absolutely no bearing on this problem. Using Reiserfs is in no way an endorsement of Hans Reiser's actions, and it's still typically a reliable, fast file system. It's open source software that can be maintained by the community, and shouldn't be discarded because of unrelated misdeeds by its creator.

---

