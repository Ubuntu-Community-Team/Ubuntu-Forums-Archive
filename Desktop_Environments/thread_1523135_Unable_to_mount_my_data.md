---
title: "Unable to mount my data"
date: 2010-07-03
forum: Desktop Environments
---

### Post by mayo1210 on 2010-07-03
sorry if this question has been asked before..
i'm using ubuntu 10.04 lucid lynx, and i install mount manager from ubuntu software center, with the aim for mounting an *.NRG file image.once i tried, i dont know how it works.
so i just open it from 

> system>administration>mount manager
then start mounting the file with choosing ntfs pastition (because i'm thinking the file *.nrg are inside ntfs partition)
then > file>apply
after i applied it there is prompt box with message 
> when you click on OK button the the program will try to replace content of the configuration file /etc/fstab and try to mount all device with sepecified option. If you start program without root rights, the program will save configuration file in you Home directory and you should replace /etc/fstab content on it by yourself

after i close that prompt, then reboot the machine, i traying to mount the ntfs partition from > places>NameNTFSpartition
the error prompt come out
> Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 3 in /etc/fstab is bad
mount: can't find /dev/sdb5 in /etc/fstab or /etc/mtab


this is content from my /etc/fstab 
> UUID=92D8351AD834FDD3 /media/my data ntfs-3g defaults 0 0
UUID=a19c9e3c-ea88-4d3b-abd8-7fc6860ca0d6 / ext4 defaults 0 1
UUID=B284C48584C44D93 /media/Pipit ntfs-3g defaults 0 0
UUID=53d9e528-8214-4134-bce5-900692c30d84 swap swap sw 0 0

can i change the configuration back, before the new fstab configured??

thx everyone for answering

---

### Post by artemyv on 2010-07-03
since you have run manager under your own user - it probably saved new fstab under your home folder - have you looked there?

Do you have the fstab in your home folder? Does it includes the new partition entry?

If yes - you will need to copy it over the system fstab using sudo cp (for example)

---

### Post by Morbius1 on 2010-07-03
>                               UUID=92D8351AD834FDD3 [COLOR=Blue]/media/my data [/COLOR]ntfs-3g defaults 0 0You can't have spaces like that in the mount point - linux hates spaces. You need to use "\040" in place of the space. THe line in fstab should look like this:
```
 UUID=92D8351AD834FDD3 /media/my\040data ntfs-3g defaults 0 0
```Then just run the following command from the terminal to see how it works:
```
sudo mount -a
```

---

### Post by mayo1210 on 2010-07-04
> **artemyv said:**
> since you have run manager under your own user - it probably saved new fstab under your home folder - have you looked there?

Do you have the fstab in your home folder? Does it includes the new partition entry?

If yes - you will need to copy it over the system fstab using sudo cp (for example)

i've been searching for fstab from my home folder, but it doesn't exist. I also have visible all hidden file

---

### Post by Morbius1 on 2010-07-04
Open a Terminal and type:
```
gksu gedit /etc/fstab
```

---

### Post by gordintoronto on 2010-07-04
NRG is a proprietary format. Do you have any reason to believe Linux can mount this format? Have a look at the Wikipedia page for NRG, which mentions a couple of programs to convert an NRG to an ISO.

---

### Post by mayo1210 on 2010-07-05
> **Morbius1 said:**
> Open a Terminal and type:
```
gksu gedit /etc/fstab
```

i've tried to change space between device name with /040

> UUID=92D8351AD834FDD3 /media/my\040data ntfs-3g defaults 0 0
UUID=92D8351AD834FDD3 /media/my\040data ntfs-3g defaults 0 0


UUID=a19c9e3c-ea88-4d3b-abd8-7fc6860ca0d6/ ext4    defaults 0 1

UUID=53d9e528-8214-4134-bce5-900692c30d84 swap    swap    sw    0    0
UUID=92D8351AD834FDD3 /media/my\040data ntfs-3g defaults 0 0
then i tried to run > sudo mount -a command.
the result:
> 
fuse: failed to access mountpoint /media/my data: No such file or directory
fuse: failed to access mountpoint /media/my data: No such file or directory
mount: mount point ext4 does not exist
fuse: failed to access mountpoint /media/my data: No such file or directory
it still not working. do you have any suggestion ?

---

### Post by mayo1210 on 2010-07-05
> **gordintoronto said:**
> NRG is a proprietary format. Do you have any reason to believe Linux can mount this format? Have a look at the Wikipedia page for NRG, which mentions a couple of programs to convert an NRG to an ISO.

i'm just searching the application through ubuntu software center, by inputing search key ***.NRG **:D
thx for your suggestion gordintotonto

nice share

---

### Post by Morbius1 on 2010-07-05
> fuse: failed to access mountpoint /media/my data: No such file or  directoryDid you create the mountpoint?
```
 sudo mkdir /media/"my data"
```

---

### Post by mayo1210 on 2010-07-05
> **Morbius1 said:**
> Did you create the mountpoint?
```
 sudo mkdir /media/"my data"
```

should i create it first..??sorry totally newbie **fool me**

---

### Post by Morbius1 on 2010-07-06
Yes you have to create the mountpoint first.

---

