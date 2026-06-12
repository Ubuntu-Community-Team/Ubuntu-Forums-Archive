---
title: "External NTFS HD and 100% CPU usage"
date: 2006-01-12
forum: General Help
---

### Post by luca.b on 2006-01-12
I have a Maxtor One Touch external HD - 180 Gb, formatted in NTFS, connected to my computer through a USB2 cable. Every time I mount it in Kubuntu CPU usage zooms up to 100% and the whole system is slowed down. The sympthoms disappear when unmounting. Unfortunately I need to keep the HD connected (it needs to be shared via Samba) and when people have to use it I'm forced to work on Windows. 
I'm not sure what triggers this, I suspect hal or gam_server. Any way to diagnose this issue better?
I'm running Kubuntu Breezy with updates.

---

### Post by Thirsteh on 2006-01-12
Mount it, open a terminal, type 'ps ax', quote the last 10 lines or so.

---

### Post by luca.b on 2006-01-12
Thanks, will report back as soon as I can reboot.

---

### Post by Thirsteh on 2006-01-12
Alright, will keep the topic open.

---

### Post by luca.b on 2006-01-12
Ok, I think I tracked down the issue. 
After trying a mount via KDE (merely clicking on the icon and waiting for it to mount, I noticed this using ps-ax:

```

9012 ?        S      0:00 /usr/bin/pmount /dev/sda1
 9052 ?        R      0:00 /bin/mount -t **udf** -o nosuid,nodev,user,async,atime,noexec,uid=1
 9199 ?        R      0:00 konsole [kdeinit]
 9245 pts/1    Ss     0:00 /bin/bash
10748 pts/1    R+     0:00 ps ax

```

(emphasis is mine)
So how in the world pmount tries to mount it as udf? How can I change this behavior?
Killing using SIGKILL (-9) the 9052 process stopped the mount, and CPU usage went back to normal.

Tracked also a second issue, when mounting manually specifying -t ntfs. It seems that df borks on ntfs volumes. Im this case I get 100% CPU usage again, and this shows up on ps ax:

```

24796 ?        S      0:00 kio_media [kdeinit] media /tmp/ksocket-lb/klauncherD2XKEa.slave
24843 ?        S      0:00 kio_system [kdeinit] system /tmp/ksocket-lb/klauncherD2XKEa.sla
24844 ?        S      0:00 kio_system [kdeinit] system /tmp/ksocket-lb/klauncherD2XKEa.sla
24845 ?        S      0:00 kio_media [kdeinit] media /tmp/ksocket-lb/klauncherD2XKEa.slave
24853 ?        S      0:00 kio_media [kdeinit] media /tmp/ksocket-lb/klauncherD2XKEa.slave
24855 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-lb/klauncherD2XKEa.slave-s
28377 ?        Ss     0:00 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l
29576 ?        R      0:00 df
29585 pts/1    R+     0:00 ps ax

```

Killing df with SIGKILL makes CPU usage go down, but it goes up agains shortly afterwards.

---

### Post by Thirsteh on 2006-01-12
You can add it to your /etc/fstab file. Example:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    noatime,errors=remount-ro 0       1
/dev/hda4       /home           ext3    noatime         0       2
# Windows partition
# /dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/sda1 /media/usb          ntfs      defaults    0    0**


Sorry for the poor formatting, but I hope I made my point. Keep in mind that the line in bold formatting is the only one I want you to look at. The others are for my system.

(Have to 'sudo gedit /etc/fstab' or similar to edit the file)

After you've done this, the automount should follow the information listed in the fstab file.

Update: Your issue seems weird. Did you try waiting it out and see if it stops eventually?

---

### Post by luca.b on 2006-01-12
[QUOTE=Thirsteh]You can add it to your /etc/fstab file. Example:
[...]
After you've done this, the automount should follow the information listed in the fstab file.[/QUOTE]

The problem is that df borks even if it's mounted manually (and CPU goes 100%). I'll try a couple more manual mounts to see if I can find a cause.
I see usage going up and down, in a cyclic manner (but mostly 100%). I suspect df is spawned by something else to monitor the disk, and since the disk is huge, with loads of files, it takes time.

```

lb@quant:~$ LC_ALL=C time df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             6.5G  3.2G  3.0G  52% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hda6              12G  803M  9.9G   8% /home
/dev/hda1              19G   11G  8.5G  55% /mnt/windows
/dev/sda1             190G   37G  154G  20% /mnt/removable
0.00user 0.48system 0:21.61elapsed 2%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+179minor)pagefaults 0swaps

```

New update, something actively accesses the disk at regular intervals:

```

lb@quant:~$ sudo umount /mnt/removable/
umount: /mnt/removable: device occupato
umount: /mnt/removable: device occupato
lb@quant:~$ sudo umount /mnt/removable/
lb@quant:~$      

```

Sorry for the Italian, I forgot LC_ALL=C, but it basically means that the device is busy (and I wasn't accessing it). Second umount worked.

---

### Post by frodon on 2006-01-12
Replace **default** by **nls=utf8,umask=0222** in the line that Thirsteh gave you if you want to access your disk as a simple user.
see : [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by luca.b on 2006-01-12
[QUOTE=frodon]Replace **default** by **nls=utf8,umask=0222** in the line that Thirsteh gave you if you want to access your disk as a simple user.
see : [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)[/QUOTE]

It doesn't prevent df from hogging the CPU, however. I will try stopping HAL, killing df and see what happens.
UPDATE: It still respawns. I wonder what could be doing this... perhaps KDE's device monitor?

---

### Post by Thirsteh on 2006-01-12
What process is using the massive amount of disk space when you plug it in? It's 'df'? Type 'top' to see.

---

### Post by luca.b on 2006-01-12
On top I see nothing suspicious save df appearing in a cyclic manner alongside usb-storage. 
By looking at the CPU monitor I believe that df is spawned, terminated  and spawned again. What I see is probably a combined result.
UPDATE: I checked and every time df appears on "top" I see it has a different PID.

EDIT: I think I have nailed the issue! It was probably my superkaramba theme that caused the mess! Removing it no longer causes df to be spawned.
It's odd though, because it wasn't monitoring the specific partition, but I guess it was relying on df to get the information, and since it was updated frequently df would bork over the size of the partition itself, causing the slowdowns.

---

### Post by Thirsteh on 2006-01-12
Haha, awkward. Glad you got it working though :)

---

