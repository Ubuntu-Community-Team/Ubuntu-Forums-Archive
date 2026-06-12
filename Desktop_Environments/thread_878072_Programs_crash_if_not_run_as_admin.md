---
title: "Programs crash if not run as admin"
date: 2008-08-02
forum: Desktop Environments
---

### Post by shmish111 on 2008-08-02
Ubuntu Hardy Heron:

At the moment, every time I click on tools -> downloads or tools -> add-ons in Firefox, it closes.  This also happens with the comic book reader Comix except it just closes as soon as I open it.  Finally, if I click on the shutdown button on the Gnome top panel, the panel closes.  However, If I run Comix or Firefox using sudo, the problem does not occur.

A month or so ago, I was running Gutsy and all of a sudden everything started closing down until the desktop was eventually just blank, no panels or programs etc.  I could do nothing.  This started happening more and more so I installed Hardy Heron from scratch.  This was fine for a while and then I started getting input/output errors and eventually no programs would work.  I had ubuntu installed on a partition of an old hard drive the rest of which was formatted as FAT32.  I thought this may be a corruption problem so I re-installed Ubuntu on another hard-drive that was formatted as ext2 and created a new partition.

I have tried swapping out the RAM and checking the CPU temp and they're fine.  Surely this must be a hardware problem, but is there any log files that might tell me more like what is happening when Firefox crashes.  Where can I go from here?

---

### Post by tamoneya on 2008-08-03
what is the output of:```
ls -l ~/.mozilla/firefox
```
Running as root via the sudo command can cause permissions errors and you probably got some permissions problems.  The above command will tell us if that is true.  The way a GUI app should be run as root is with gksudo (ubuntu) or kdesudo (kubuntu) like so:```
gksudo firefox
```

---

### Post by shmish111 on 2008-08-03
Thanks for your reply.  Unfortunately it seems that I am a retard...  I have only 490Mb of free space on the root partition.  I guess the primary user account is allocated only some of this space so it has run out of space.  When I run programs as root I suppose I am allocated some extra space.  I discovered this by running Open Office and getting some sort of low memory error.

Now the problem is, how can I resize the root partition as I obviously can't unmount it when running the OS.  Cant I use the LiveCD?

---

### Post by tamoneya on 2008-08-03
yes the liveCD is how you fix this.  Run the liveCD and there is a program called gparted which should be preinstalled.  If it isnt it can be installed through synaptic/add remove.  Hit alt-F2 and run:```
gksudo gparted
```
Then you will get a graphical interface for making, deleting and resizing partitions.

---

