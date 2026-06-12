---
title: "New install two minor issue"
date: 2015-01-01
forum: Desktop Environments
---

### Post by xendistar2 on 2015-01-01
I have done a new install of xubuntu 14:10 on my wife's PC but I have two minor issues. First I can't permanently get rid of the floppy icon, I can remove the icon on a per session basis by typing "sudo rmmod floppy! This will immediately remove the floppy icon from the desktop but it will reappear on a reboot. I have the floppy module blacklisted in /etc/modprobe.d/blacklist.conf 

Secondly I am trying to get a photo on the users account so that when they login their picture is showing where they login. I have produced the photo (it actually smaller than the 96x72 required), placed it in the root of the users home folder and called it .face.png but when they login the photo is not used. I know this works as I am using XFCE on a Debian based distro and that how I do it on my PC.

Any suggestions on these please

---

### Post by Bashing-om on 2015-01-01
xendistar2; Hi !

For the 1st situatoion of the OS loading up a floppy disk:
Disable floppy seek in bios, so that the hardware is not passed onto the Operating system,
AND
edit the file " /etc/fstab " and comment out the line(s) that reference 'fd0' .
If you are not comfortable making this edit, post back the output of terminal command:
```

cat /etc/fstab

``` and we will provide specific instruction.

For the .png image , sorry I do not have the experience to be of direct help.
Maybe:
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Will provide the answer to your quest .

[INDENT][INDENT][INDENT]we can do that 
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-01-01
The file is put into /home/username/ and it is simply named .face without any file type. It most probably has to be a png image but the file type is not needed in the file name.

Regards.

---

### Post by xendistar2 on 2015-01-01
> **Bashing-om said:**
> xendistar2; Hi !

For the 1st situatoion of the OS loading up a floppy disk:
Disable floppy seek in bios, so that the hardware is not passed onto the Operating system,
AND
edit the file " /etc/fstab " and comment out the line(s) that reference 'fd0' .
If you are not comfortable making this edit, post back the output of terminal command:
```

cat /etc/fstab

``` and we will provide specific instruction.

For the .png image , sorry I do not have the experience to be of direct help.
Maybe:
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Will provide the answer to your quest .
[INDENT][INDENT][INDENT]we can do that 
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing, the Floppy option has been disabled in bios (not that there is one fitted) and there is no fd0 in /etc/fstab, they were the first places I checked, I can't even find a option to remove icon from the desktop (in the same way as you can stop removable drive being placed on the desktop).

---

### Post by xendistar2 on 2015-01-01
> **grahammechanical said:**
> The file is put into /home/username/ and it is simply named .face without any file type. It most probably has to be a png image but the file type is not needed in the file name.

Regards.

Thanks GC, I had it listed as face.png, deleted the .png bit and everything is working

Thanks

---

### Post by Bashing-om on 2015-01-01
xendistar2; Humm ... 

On my box I do not have a floppy drive either, but bios does have that provision. I must disable "floppy seek" in bios.
When I disable "floppy seek" I no longer get that icon on the desk top .

I also had to initially remove that bad entry for a floppy drive from my /etc/fstab file.
What does :
```

mount
cat /etc/mtab

```
relate about the presence of a floppy drive ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by xendistar2 on 2015-01-02
> **Bashing-om said:**
> xendistar2; Humm ... 

On my box I do not have a floppy drive either, but bios does have that provision. I must disable "floppy seek" in bios.
When I disable "floppy seek" I no longer get that icon on the desk top .

I also had to initially remove that bad entry for a floppy drive from my /etc/fstab file.
What does :
```

mount
cat /etc/mtab

```
relate about the presence of a floppy drive ?[INDENT][INDENT]gotta be a cause
[/INDENT]
[/INDENT]


Here is the result of cat /etc/mtab

```
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0proc /proc proc rw,nodev,noexec,nosuid 0 0
sysfs /sys sysfs rw,nodev,noexec,nosuid 0 0
none /sys/fs/cgroup tmpfs rw,uid=0,gid=0,mode=0755,size=1024 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,nodev,noexec,nosuid,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,nodev,noexec,nosuid,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sda1 /media/backups ext4 rw 0 0
/dev/sdb2 /home ext4 rw 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,nosuid,noexec,nodev,none,name=systemd 0 0
192.168.0.68:/volume1/Data /media/nfs nfs rw,noexec,nosuid,nodev,vers=4,addr=192.168.0.68,clientaddr=192.168.0.63 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=karen 0 0


```

Still can't see any listing of the floppy drive

---

### Post by Bashing-om on 2015-01-02
xendistar2; Umphh //

It is frowned upon here to respond with " I do not know" as it adds nothing to the resolution of the thread. But I must .
That is the extent of my knowledge. Perhaps others with a deeper understanding of the operating system can explain why there is floppy disk recognition.

I too would be interested to know .

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by xendistar2 on 2015-01-02
Thanks for attempting to help Bashing, you did what you could so don't be afraid to admit you don't know, I had to admit I don't know when I posted on here. At the moment the PC runs 24\7 so it only when it is rebooted that the icon reappears. In the short term a simple rmmod floppy sorts out the issue.

Thanks again for the help

---

