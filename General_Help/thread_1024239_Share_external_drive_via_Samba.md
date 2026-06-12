---
title: "Share external drive via Samba"
date: 2008-12-28
forum: General Help
---

### Post by brandonhon on 2008-12-28
i have an external drive hooked up to my computer that i want to share with samba. i do not have anything in my fstab to mount it at boot it just auto mounts after boot up.

my problem is that i can see the drive but when i try to connect to it is says "failed cannot mount windows share". it will not mount on my macbook either. here is the share in my smb.conf

[movies]
        comment = movies
        path = /media/400G-MOVIES/movies
	browseable = yes
	guest ok = yes
	public = yes
	writable = yes

any suggestions? i also tried suggestions from a couple other posts and nothing worked

---

### Post by xjcannonx on 2008-12-30
do you have ntfs-config installed? its in the repo's

---

### Post by brandonhon on 2008-12-30
yes, i believe it is standard these days.

---

### Post by dcstar on 2008-12-30
> **brandonhon said:**
> i have an external drive hooked up to my computer that i want to share with samba. i do not have anything in my fstab to mount it at boot it just auto mounts after boot up.

my problem is that i can see the drive but when i try to connect to it is says "failed cannot mount windows share". it will not mount on my macbook either. here is the share in my smb.conf

[movies]
        comment = movies
        path = /media/400G-MOVIES/movies
	browseable = yes
	guest ok = yes
	public = yes
	writable = yes

any suggestions? i also tried suggestions from a couple other posts and nothing worked

This is the relevant section of an external drive (labelled "DCSTAR") which works with my Samba setup:
```
[DCSTAR]
path = /media/DCSTAR
guest ok = yes
valid users = sharer
read only = No
create mask = 0777
directory mask = 0777
available = yes
browsable = yes
public = yes
writable = yes
```

I have one valid Samba user: "sharer" which has a password, but I could have more.

---

### Post by brandonhon on 2008-12-31
the only difference between yours and mine is the 

available = yes

I will try this and see if it works, thanks. by the way i want everyone to have access to the drive not just one person

---

### Post by brandonhon on 2009-01-02
ok, i tried adding the line 

available = yes

nothing happened. it still won't let me connect to it. here is my entire smb.conf let me know if you see anything wrong.

```

[global]
	workgroup = foonet
	guest account = nobody
	keep alive = 30
	os level = 65 
	kernel oplocks = false
	security = share
	encrypt passwords = yes
	printing = cups
	printcap name = cups
	load printers = yes
	socket options = TCP_NODELAY
	map to guest = Bad User
	local master = yes   
	wins support = yes
	server string = %h server (Samba, Ubuntu)

[movies]
	comment = movies
	path = /media/400G-MOVIES/movies
	browseable = yes
	guest ok = yes
	public = yes
	writable = yes
	available = yes

```

---

### Post by brandonhon on 2009-01-02
after looking around is this an automount issue with the external drive? do i have to add the drive to my fstab?

---

### Post by albinootje on 2009-01-02
> **brandonhon said:**
> after looking around is this an automount issue with the external drive? do i have to add the drive to my fstab?

Samba is not gonna automatically mount it for you.
But you wrote that it's mounted when you plug it in, right ?
So that should not be an issue.

A question, can your normal user read the drive properly ?
You have guest=nobody in your samba configuration, can the non privileged user nobody also read it ? Just wondering.

Can you post the following after plugging that usb-drive in :
```

mount
cat /etc/fstab

```

Ubuntu Intrepid started offering a guest account where the user is called guest, could that perhaps lead to problems ?

---

### Post by brandonhon on 2009-01-03
i tried the guest session and i cannot view the drive. it tells me that i don't have the correct permissions.

here is my fstab

```

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5b080f55-6a3e-49b0-b9bd-d2a9612e4830 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f63e2ae8-eaed-406b-9bdb-8cff5d2642c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by dcstar on 2009-01-03
When you plug in your external drive it should appear in /media with full R/W permissions.

The files/directories on the drive should also have appropriate permissions.

Please be aware that when you make changes to the smb.conf file you will have to restart your samba with the following (so it loads the new config):

```
sudo /etc/init.d/samba restart
```

---

### Post by brandonhon on 2009-01-03
i have restarted samba. and still nothing. here is what it gives me for ls -l under media.

drwx------ 4 xx   root 16384 1969-12-31 18:00 400G-MOVIES

i have also tried chmoding the drive to 777 and still nothing.

---

### Post by albinootje on 2009-01-04
> **brandonhon said:**
> i have restarted samba. and still nothing. here is what it gives me for ls -l under media.

drwx------ 4 xx   root 16384 1969-12-31 18:00 400G-MOVIES

i have also tried chmoding the drive to 777 and still nothing.

You need to make sure that this drive gets mounted with the right permissions for those who are needing to read and write one it.

Did you do a :
```

sudo chmod 755 /media/400G-MOVIES/

```
That should give anyone the right to navigate into the /media/400G-MOVIES directory.
The drwx------ means that only root can do that.

Or what did you do ?

---

### Post by brandonhon on 2009-01-04
yep, i tried that too. here is exactly what i tried and here is the ls -l result

```
sudo chmod -R 777 /media/400G-MOVIES/
```

i also tried 755. this is my result

> drwx------ 4 xx   root 16384 1969-12-31 18:00 400G-MOVIES

---

### Post by albinootje on 2009-01-04
> **brandonhon said:**
> yep, i tried that too. here is exactly what i tried and here is the ls -l result

```
sudo chmod -R 777 /media/400G-MOVIES/
```

i also tried 755. this is my result

Can you please post the following, when the drive is attached and mounted :
```

mount
cat /etc/fstab

```
Thanks.

---

### Post by brandonhon on 2009-01-04
my fstab is shown above but here it is again:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5b080f55-6a3e-49b0-b9bd-d2a9612e4830 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f63e2ae8-eaed-406b-9bdb-8cff5d2642c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


the drive is currently mounted and can be seen as a mount on my desktop. i can also connect to the drive and have read/write permissions.

---

### Post by albinootje on 2009-01-05
> **brandonhon said:**
>  the drive is currently mounted and can be seen as a mount on my desktop. i can also connect to the drive and have read/write permissions.

Can you post the output of this command when the drive is in and mounted :
```

mount

```

---

### Post by brandonhon on 2009-01-05
sorry bout that, here you go.

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bh)
/dev/sdb1 on /media/400G-MOVIES type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
none on /tmp/guest-home.S29756 type tmpfs (rw,mode=700)
```

---

### Post by linux6994 on 2009-01-05
I have an external usb drive that has everyones stuff on it including my sbackup files. I have installed system-config-samba its a gui for your smb.conf. makes things real easy . . .

---

### Post by brandonhon on 2009-01-07
nope the gui didn't work. thanks though. i think it has something to do with the way the automount works.

i don't think the drive gets read/write permissions for everyone, just the user that the drive mounts under. i think this part in the output of my mount command might be the problem.

```
/dev/sdb1 on /media/400G-MOVIES type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,**umask=077**,flush)

```

i believe the umask needs to be 000 not 077, but how do i change that if it is automounted? do i just have to add the drive to my fstab?

---

### Post by brandonhon on 2009-01-07
Woohoo! Got it. I found that the automount sets permissions for root access to the drive. To fix it I just added ```
umask=000
``` to the mount option under the drive properties. I could also do this by entering my drive in fstab with the same umask. Hope this helps someone later on.

Thanks for all the help

---

