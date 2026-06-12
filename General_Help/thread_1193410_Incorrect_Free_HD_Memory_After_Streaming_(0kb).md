---
title: "Incorrect Free HD Memory After Streaming (0kb)"
date: 2009-06-21
forum: General Help
---

### Post by scu-ba-de-buntu on 2009-06-21
Sometimes after watching something on Hulu.com (or youtube but not as much), Ubuntu 64bit 8.04 (with all updates) decides that there is no free hard drive space until some random time. Normally I just let it run its course (about a week), but I need to program something right now and want to know is there a way to fix this. It is a real show stopper. I tried forcing touch fsck, but it didn't help. Every time I need to do anything on this computer I am forced to delete something, even though there should be about 20GB free. Once the computer decides to mess up on HD memory, it slowly dispersals by just being used. Even browsing the harddrive can cause it to go back to 0kb free. At that point nothing works again and something has to be moved to a USB thumbdrive and the HD copy deleted. That is how I logged into this forum.

I have the Ubuntu Studio set installed, but this happened before installing also. It may have something to do with a memory allocation problem in Flash - where the video is cached but not properly deleted after quiting firefox.

Extra Info:

Dell Inspiron 1501 Laptop, AMD64 Dual Core, Multi-OS, ~1 year old Ubuntu Install,     

Depending on which software I am using, I sometimes use the ATi Graphics Driver. I am currently not using it.

```

File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r159

```
```

lsb_release -a 
LSB Version:	core-2.0-amd64:core-3.0-amd64:core-3.1-amd64:core-3.2-amd64:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch:cxx-2.0-amd64:cxx-3.0-amd64:cxx-3.1-amd64:cxx-3.2-amd64:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-3.2-noarch:desktop-3.1-amd64:desktop-3.2-amd64:desktop-3.1-noarch:desktop-3.2-noarch:graphics-2.0-amd64:graphics-3.0-amd64:graphics-3.1-amd64:graphics-3.2-amd64:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3.1-noarch:graphics-3.2-noarch:languages-3.2-amd64:languages-3.2-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:printing-3.2-amd64:printing-3.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

``````

free
             total       used       free     shared    buffers     cached
Mem:       1912900     919784     993116          0      27452     504960
-/+ buffers/cache:     387372    1525528
Swap:      5052400          0    5052400

```


Any Ideas?? :confused:

Thanks

---

### Post by sdennie on 2009-06-21
What is the output of "df" when you see the problem?

---

### Post by scu-ba-de-buntu on 2009-06-21
```

$ df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            117338060 111424712         0 100% /
varrun                  956448       124    956324   1% /var/run
varlock                 956448         0    956448   0% /var/lock
udev                    956448        56    956392   1% /dev
devshm                  956448         0    956448   0% /dev/shm
lrm                     956448     45736    910712   5% /lib/modules/2.6.24-24-rt/volatile
overflow                  1024        16      1008   2% /tmp
gvfs-fuse-daemon     117338060 111424712         0 100% /home/muser/.gvfs

```

and after deleting a Linux iso I was working on (~1Gb) so I could log into this site.

```

df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            117338060 110403088   1021448 100% /
varrun                  956448       136    956312   1% /var/run
varlock                 956448         0    956448   0% /var/lock
udev                    956448        56    956392   1% /dev
devshm                  956448         0    956448   0% /dev/shm
lrm                     956448     45736    910712   5% /lib/modules/2.6.24-24-rt/volatile
overflow                  1024        40       984   4% /tmp
gvfs-fuse-daemon     117338060 110403088   1021448 100% /home/muser/.gvfs

```

---

### Post by scu-ba-de-buntu on 2009-06-22
Ok, it is going back to normal, but I still want to know how to force it to self-correct next time. I checked about 20 minutes ago and I had 500mb. Then it went to 0mb, and later 6Gb and right now it says I have 11Gb free and is rising back to the correct value. Does anyone know anything about this or the program which calculates free space?

---

