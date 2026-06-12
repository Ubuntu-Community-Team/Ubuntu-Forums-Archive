---
title: "HD Mounting"
date: 2005-06-02
forum: Desktop Environments
---

### Post by master of all on 2005-06-02
How do I do it on Kubuntu? Is the comand line ```
sudo mount /dev/hda* /mnt/windows -o umask=000
``````
*=HDA number
``` this? Because if it is then it's mounting it but not letting me view the files. All I need is it mounting and to be able to view the files. Also is there fstab in kubuntu or if not whatever the equivalent is to get the drive to mount on startup.

[SIZE=1]Sorry if this doesn't make much sense. Early in the morning for me.[/SIZE]

---

### Post by pdk001 on 2005-06-02
sudo mount /dev/hda* /media/windows(choose dir where you wanted) -t ntfs -o umask=0222

---

### Post by kvidell on 2005-06-02
[QUOTE=master of all]How do I do it on Kubuntu? Is the comand line ```
sudo mount /dev/hda* /mnt/windows -o umask=000
``````
*=HDA number
``` this? Because if it is then it's mounting it but not letting me view the files. All I need is it mounting and to be able to view the files. Also is there fstab in kubuntu or if not whatever the equivalent is to get the drive to mount on startup.

[SIZE=1]Sorry if this doesn't make much sense. Early in the morning for me.[/SIZE][/QUOTE]
 FSTAB is always available on Linux systems as /etc/fstab
as for that command... I'm not sure on the syntax exepectance but I always put all options and flags before arguments.
So, I would do it like this:

sudo mount -o umask=000 /dev/hda1 /mnt/windows

AFAIK you ~must~ specify a partition number. I may be wrong though.
Also, if it's NTFS then you might do well to include -t ntfs between "mount" and "- o"

HTH
- Kev

---

### Post by improverrr on 2005-06-02
as mentioned above, you can add this line to /etc/fstab:

/dev/hda*	/PATH		vfat	defaults,uid=1000,gid=100,umask=022	0	0

* = HDA number, probably 5

do this while in root, then in console (as root) do the following command:

mount -a

this remounts everything from the FSTAB and should be working now, and now auto mount at login.

---

### Post by master of all on 2005-06-02
Thanks. It mounts now. But for editing fstab, I need root permissions. How am I to get that?

---

### Post by Rodrigo on 2005-06-02
sudo gedit /etc/fstab

or

search for visudo

or

su

or

sudo su


remember google is your friend, and make some searches in the forum, AND read THIS [http://ubuntuguide.org/](http://ubuntuguide.org/), the unofficial ubuntu starter guide

---

