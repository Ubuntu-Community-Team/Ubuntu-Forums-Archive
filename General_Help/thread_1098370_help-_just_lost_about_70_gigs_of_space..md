---
title: "help- just lost about 70 gigs of space."
date: 2009-03-16
forum: General Help
---

### Post by twitch2197 on 2009-03-16
i had ubuntu, and i installed kubuntu in my system. i installed the "kde" package and now i have about 70 gigabytes less on my computer. is the kde package what took up that much space?

---

### Post by circa82 on 2009-03-17
First off, Kubuntu is Ubuntu using KDE. You shouldn't need to install KDE on Kubuntu. 

Can you explain a bit further as far as how these were installed? Separate partitions? Same partition? Was Kubuntu a fresh install? You should not have used 70GB of disk space.

---

### Post by mb_webguy on 2009-03-17
Use a Disk Usage Analyzer (either Baobab or KDirStat, which you can find in Applications->Accessories) to see what's eating up all of your drive space.

*Nothing* in Linux should use even 7GB, much less 70GB.  Linux applications tend to be tiny compared to Windows equivalents.  I have both the Gnome and KDE desktops installed along with a large number of applications, and my entire installation totals about 6GB.

---

### Post by fieroboom on 2009-03-17
> **twitch2197 said:**
> i had ubuntu, and i installed kubuntu in my system. i installed the "kde" package and now i have about 70 gigabytes less on my computer. is the kde package what took up that much space?

From the information given, it sounds like you most likely let the installer do it's "guided" partitioning, which kept the original data (and partitions) you had on the disk from ubuntu + GDM.
However, this could be misinformation, because what you provided isn't *quite* enough to solve your issue...

Questions to answer:
- Did you simply install the KDE environment, or did you pop in a 'Kubuntu' installer disc and install from there?
- Can you post some more info about your drives?

**Least possibly destructive (ie, you can't mess your system up):**

You can run the command 'df -h' as a normal user like this to see what partitions are being used, and how much space they're using (this doesn't show my NTFS partition, nor my swap space):

```
paul@paul-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              77G  6.1G   67G   9% /
tmpfs                 980M     0  980M   0% /lib/init/rw
varrun                980M  104K  980M   1% /var/run
varlock               980M     0  980M   0% /var/lock
udev                  980M  2.7M  978M   1% /dev
tmpfs                 980M     0  980M   0% /dev/shm
lrm                   980M  2.0M  978M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             942M   41M  854M   5% /boot
```

**Slightly more possibly destructive if you mess up:**

You can run gparted like so:

```
paul@paul-desktop:~$ sudo gparted
```

You need to run it as superuser (sudo or kdesu), but _DO NOT_ change anything!! :D Just run it, take a screenshot, and close it. Your screenshot might look something similar to this:

[img]http://southeastfieros.com/gparted-screenie.png[/img]

**Most possibly destructive if you mess up:**

If you're more comfortable in a terminal, then you can run cfdisk, then copy the output, and paste it here, like so:

```
paul@paul-desktop:~$ sudo cfdisk /dev/sda

                                                                                        cfdisk (util-linux-ng 2.14)

                                                                                           Disk Drive: /dev/sda
                                                                                    Size: 320072933376 bytes, 320.0 GB
                                                                           Heads: 255   Sectors per Track: 63   Cylinders: 38913

          Name                          Flags                         Part Type                 FS Type                                   [Label]                             Size (MB)
 ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          sda1                          Boot                           Primary                  Linux ext3                                                                      1003.49
          sda3                                                         Primary                  Linux swap / Solaris                                                            1003.49
          sda4                                                         Primary                  Linux ext3                                [root]                               83889.64
          sda2                                                         Primary                  NTFS                                      []                                  234173.73

```

If you can provide a few more details, I'm sure we can get you fixed up! Let us know what you find ;)
-Paul

---

