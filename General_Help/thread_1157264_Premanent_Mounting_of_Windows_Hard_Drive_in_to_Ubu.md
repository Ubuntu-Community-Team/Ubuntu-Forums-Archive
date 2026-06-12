---
title: "Premanent Mounting of Windows Hard Drive in to Ubuntu"
date: 2009-05-12
forum: General Help
---

### Post by lrwfairs on 2009-05-12
Recently, I have learned how to gain access to a Windows hard drive from Xubuntu through the Terminal (See [http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/)).

However, every time I reboot my system, I have remount the hard drive in order to gain access. I was wondering if there is a way to permanently mount a Windows hard drive in Xubuntu so I do not have to continually run through the Terminal to gain access.

Thank you in advance.

Lucas

---

### Post by Elfy on 2009-05-12
Simple way is to install ntfs-config ```
sudo apt-get install ntfs-config
```

Then use the tool to add the ntfs drive to fstab, it will get mounted on reboot from then on.

---

### Post by uupreti on 2009-05-12
There is a software called Pysdm which allows you to decide which drives to mount or unmount during startup. Pysdm is an GUI application and is extremely easy to use.

Command to install it

**"sudo apt-get install pysdm**"

Command to run it after install

[B]"sudo pysdm"

OR 

[/B]If you don't want to use this software, you can write mounting line to /etc/rc.local script file which is executed at system startup time.[B] ( providing you have enough access to run this command)
[/B]

---

### Post by Elfy on 2009-05-12
> If you don't want to use this software, you can write mounting line to /etc/rc.local script file which is executed at system startup time.I always use /etc/fstab to mount partitions.

---

### Post by Penguin Guy on 2009-05-12
> **forestpixie said:**
> I always use /etc/fstab to mount partitions.
+1 - Yes; if you know what you're doing then I would use fstab. Otherwise; try some of the programs listed above.

---

### Post by uupreti on 2009-05-12
Yeah I agree with [[COLOR=#d40000]**forestpixie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428"). It's better to use **fstab** file to mount filesystem. I just wanted to give him idea about startup script file. I always edit **fstab** manually when I use **centos, redhat** where GUI is not so much preferred in sever system.

---

### Post by veli on 2009-05-12
To mount vfat with read/write access put the following line in your fstab. Please change sda2 to your windows partition.

```
/dev/sda2                                  /media/sda2    vfat         users,rw,umask=000          0  0 
```

---

### Post by Elfy on 2009-05-12
Heh - the > I always use /etc/fstab to mount partitions. was more aimed at the previous post (although that is what I do) - I couldn't see the need to be using /etc/rc.local.

As I said I would use ntfs-config, but the pysdm is also a good choice - certainly both are a bit easier than editing fstab first time around - I did.

---

### Post by sepius on 2009-05-24
uupreti
Psydm

Thanks for that.  It is really an easy little program and allows you to customise the mount string in fstab anyway if need be.  Worked perfect for me.:D

Thanks again.

---

