---
title: "Adding a new hard drive."
date: 2006-06-06
forum: Desktop Environments
---

### Post by eddorey2k3 on 2006-06-06
Ugh. This *should* have been so simple.. ](*,) 

Anyway. Added another hard drive to my machine (Only had a 40gb drive before, added another one) so I can store mp3's on the 40gb drive. I followed a tutorial at [http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/]("http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/") all the way to the end, but once I finally come to trying to mount the partition I get 

```

ed@kubuntu:~$ sudo mount /dev/hdc1
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

This happens with a variety of mount commands, including if I change the location of where it's going to be mounted to in /etc/fstab.

I then tried to do it with the "Disk and Filesystems" thinger in System, but that gives the same error (Although it lets me change the mounting point to something a lot more useful (/home/ed/mp3)(It didn't occur to me the first time :P))

Any ideas? >_>

---

### Post by eddorey2k3 on 2006-06-06
Ok. Quick update! I changed a setting in Config > Options > Advanced from "Default" to "defaults" and it now lets me mount the disk! However, it won't let me write to the directory (/home/ed/mp3). I did notice it was because it's owned by root though. Might this be causing it, and what's the best way to take ownership? Chmod?

---

### Post by tonyr on 2006-06-06
I'm not really sure what you are doing here.  Are you using Ubuntu(Gnome, brown) or
Kubuntu(KDE, blue)? I would have thought that the new drive
would show up as **/dev/hdb**, not **/dev/hdc**.  In a terminal, type 
```

sudo lshw -C disk

```

and post the results here.  Then have a look at [http://wiki.ubuntu.com/InstallingANewHardDrive]("http://wiki.ubuntu.com/InstallingANewHardDrive")

---

### Post by tpratt on 2006-06-06
I assume you are mounting hdc1 to /home/ed/mp3 and that your username is ed:

  cd /home/ed/mp3
  sudo chown -R ed .

should give you access to write to your new disk.

---

### Post by eddorey2k3 on 2006-06-06
[QUOTE=tpratt]I assume you are mounting hdc1 to /home/ed/mp3 and that your username is ed:

  cd /home/ed/mp3
  sudo chown -R ed .

should give you access to write to your new disk.[/QUOTE]

That's the ticket. Thanks, bro.

---

### Post by eddorey2k3 on 2006-06-06
[QUOTE=tonyr]I'm not really sure what you are doing here.  Are you using Ubuntu(Gnome, brown) or
Kubuntu(KDE, blue)? I would have thought that the new drive
would show up as **/dev/hdb**, not **/dev/hdc**.  In a terminal, type 
```

sudo lshw -C disk

```

and post the results here.  Then have a look at [http://wiki.ubuntu.com/InstallingANewHardDrive]("http://wiki.ubuntu.com/InstallingANewHardDrive")[/QUOTE]

It's Kubuntu. Hence the Kubuntu tag ;) It's showing up as hdc because of how the IDE is set up, and because it was added after the CD Drive. The CD drive already uses the other mnt point. (Default Dapper installer did it.)

---

