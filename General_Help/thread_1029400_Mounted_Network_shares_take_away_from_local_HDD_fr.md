---
title: "Mounted Network shares take away from local HDD free space?"
date: 2009-01-03
forum: General Help
---

### Post by jimmah6786 on 2009-01-03
Something very Interesting  is going on with my system.

I just installed Ubuntu 8.10 and the only changes I have made to it were to install mythtv, and to add 4 lines to the /etc/fstab (see below). Keeping in mind that this is a 500GB HDD, when I try to copy files from any type of media(network, DVDs, etc) I cannot because it says that it is out of free space?. The files I am copying are not over 500GB!!! What is strange is I tend to find it only says I am out of free space when I have the 4 network locations mounted.

Any way, thank you for taking the time to look at this issue I am having.

Cheers,

Jim
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ae62a227-5b8b-4bba-8097-111feaed0531 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=5a1958df-be93-4ff4-998f-d1aac8d10028 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=ae5c1054-85b1-48e2-989f-bff7a60e884d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
\\192.168.254.250\Volume_2	/home/mythuser/Desktop/Videos/Movies1	cifs	user=xxxx,password=xxxx 0 0
\\192.168.254.250\Volume_1\Movies	/home/mythuser/Desktop/Videos/Movies2	cifs	user=xxxx,password=xxxx	0	0
\\192.168.254.250\tv	/home/mythuser/Desktop/Videos/TV	cifs	user=xxxx,password=xxxx	0	0
\\192.168.254.250\Music	/var/lib/mythtv/music/	cifs	user=xxxx,password=xxxx 	0	0


```

df -h renders
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G   11G     0 100% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  364K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.8M 1002M   1% /dev
tmpfs                1004M     0 1004M   0% /dev/shm
lrm                  1004M  2.4M 1002M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             454G   20G  435G   5% /var/lib
//192.168.254.250/Music
                      916G  301G  616G  33% /var/lib/mythtv/music
//192.168.254.250/Music
                      916G  301G  616G  33% /var/lib/mythtv/music
//192.168.254.250/Volume_2
                      916G  912G  4.3G 100% /home/mythuser/Desktop/Videos/Movies1
//192.168.254.250/Volume_1/Movies
                      916G  301G  616G  33% /home/mythuser/Desktop/Videos/Movies2
//192.168.254.250/Music
                      916G  301G  616G  33% /var/lib/mythtv/music
//192.168.254.250/Volume_1/Movies
                      916G  301G  616G  33% /home/mythuser/Desktop/Videos/Movies2
//192.168.254.250/tv  916G  301G  616G  33% /home/mythuser/Desktop/Videos/TV
//192.168.254.250/Music
                      916G  301G  616G  33% /var/lib/mythtv/music
/dev/scd0              23G   23G     0 100% /media/cdrom0

```

---

### Post by taurus on 2009-01-03
> 
\\192.168.254.250\Music	/var/lib/mythtv/music/  	cifs	user=xxxx,password=xxxx 	0	0

Do you really mean to mount that to /var/lib/mythtv/music instead of /home/mythuser/Desktop/music?

---

### Post by jimmah6786 on 2009-01-03
> **taurus said:**
> Do you really mean to mount that to /var/lib/mythtv/music instead of /home/mythuser/Desktop/music?

Yes, I don't have a music folder on the mythuser's desktop. Yet. I will though. Music folder is only 80GB, so still should not be saying I am out of disk space.

Also, when I try to install packages, I am getting no space left of device. So I cannot install/remove anything!! VERY STRANGE

---

### Post by plucky on 2009-01-03
> /dev/sda1              12G   11G     0 100% /



Could that be the problem?

Good Luck

---

### Post by jimmah6786 on 2009-01-04
> **plucky said:**
> Could that be the problem?

Good Luck

Or Anwser me this, when you mount a drive to a folder on your system, does that mess up the calculation of free space?

---

