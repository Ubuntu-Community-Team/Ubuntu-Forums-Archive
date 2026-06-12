---
title: "/home partition after re-install OS"
date: 2010-12-16
forum: Desktop Environments
---

### Post by b1235762 on 2010-12-16
I have to re-install ubuntu 10.04.
I run Ubuntu 8.10 Livecd and manually set partition table. used old /home partition and didnt format it.
After I installed 8.10 I upgraded it  >9.04 >9.10 >and 10.04 LTS wchich I prefer(couse its LTS)
This old /home partition stayed, but now its as mountable 99GB filesystem. How to make it my /home folder now?

---

### Post by amsterdamharu on 2010-12-16
Do you know which /dev/sd? it is? If not you can type the following command:
```
sudo fdisk -l
```

Then the following command:
```
blkid
```
Copy and paste the id of your home partition, now press alt + F2 and type:
```
gksu gedit
```
Open up the file /etc/fstab and add the following line:
```
UUID=[your copied UUID without the quotes]     /home   ext3   errors=remount-ro 0       1
```
I assume your home partition is ext3 but you can know for sure checking the blkid command you did before, if it's ext4 just replace ext3 with ext4.

Now save it and reboot.

---

### Post by b1235762 on 2010-12-16
after doing exacly by you, system doesnt boot. it says partition are wrong. dont have gksu file,its empty.

---

### Post by drs305 on 2010-12-16
What *amsterdamharu* wanted you to do was to open /etc/fstab using the "gksu gedit" command:
```
gksu gedit /etc/fstab
```

If you can't boot normally, are you given an option during boot to press S to skip mounting certain partitions? If they are non-system partitions your system should boot.

If your system partitions are incorrect, boot the LiveCD, then mount your Ubuntu partition, then use the following command to do what *amsterdamharu* suggested.
```

sudo mount /dev/sdXY /mnt  # sda1, sdb5, etc. Whatever your Ubuntu partition is.
gksu gedit /mnt/etc/fstab
```

If it still  doesn't boot, you may have a new /home within the installation which will boot. To see, open fstab as above and place a # symbol at the start of the /home line. This will disable it and if your new install has it's own usable /home it may boot that way.

---

### Post by amsterdamharu on 2010-12-16
I am sorry to hear your system doesn't boot anymore, can you boot off a live cd and give me the output of:
```
blkid
```

Do you know where Ubuntu is installed and where home is installed? If not I can help you find out by posting the commands here.
You can copy and paste the commands from your browser to a terminal. I will go to bed soon so maybe you're going to have to wait until tomorrow, sorry but maybe some else can help you.

---

### Post by b1235762 on 2010-12-16
to be clear, system didnt boot. now it does. I fix it. but problem with that home partition still is to solve.

---

### Post by amsterdamharu on 2010-12-16
Could you post the output of blkid?

Maybe the content of /etc/fstab as well that way I can change it to a value that you need.

---

### Post by b1235762 on 2010-12-27
[html]
root@xxx:/home/xxx# blkid
/dev/sda5: UUID="23684f08-e79f-4555-83ee-4146b737b946" TYPE="ext4" 
/dev/sda6: UUID="a1fb7052-39a9-494e-a257-579a4b136c49" TYPE="ext3" 
/dev/sda7: UUID="108dd6fe-7790-4ee5-ac96-cebed1e86d15" TYPE="swap" 
root@xxx:/home/xxx# 
[/html][html]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a1fb7052-39a9-494e-a257-579a4b136c49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=108dd6fe-7790-4ee5-ac96-cebed1e86d15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 [/html]

---

### Post by amsterdamharu on 2010-12-27
Ok, you can execute the following command:

```
gksu gedit /etc/fstab
```Add the following line at the end:

```
UUID=23684f08-e79f-4555-83ee-4146b737b946 /home   ext4   errors=remount-ro 0       1
```Safe the file and reboot.

---

