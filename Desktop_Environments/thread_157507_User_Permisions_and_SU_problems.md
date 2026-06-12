---
title: "User Permisions and SU problems"
date: 2006-04-09
forum: Desktop Environments
---

### Post by claets99 on 2006-04-09
Hello, ive just installed ubuntu and  i can see my ntfs windows drives on the desktop but when i go to access them i get this message:

[IMG]http://www.lemonbrook.com/screenshot1.png[/IMG]

now ive searched around on google and it says something about the user. so i try to go to users and groups but it wont load up. the username i created with the installation was nick and i know the password (also the password is correct when i type it in  - its only a simple one) when i go to terminal ande type su i get this...

> nick@ubuntu:~$ su
Password:
su: Authentication failure
Sorry.
nick@ubuntu:~$


im really confused. i cannot do many commands from the terminal window such as su apt-get update, etc etc.

Any help would be brilliant.
Thanks, clarets99

---

### Post by aysiu on 2006-04-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by stanthecaddy22 on 2006-04-09
You cannot use the su command because the root account by default does not technically have a password. For individual commands use "sudo [commandname]" to run as root. If you want to be able to use su to logi n as root you will need to set a root password by using "sudo passwd root".

---

### Post by claets99 on 2006-04-09
thank you both for your help.

@ stanthecaddy22: would this mean that there would be no login screen and i would just go striaght to the desktop at startup?

thank you

EDIT: I have tried to unmount but nothing is happening in the terminal. i try typing in sudo fdisk -l nothing appears. 
> nick@ubuntu:~$ sudo umount /media/sda1
nick@ubuntu:~$ sudo umount /media/sda5
nick@ubuntu:~$ sudo umount /media/sda6
nick@ubuntu:~$ sudo fdisk -l
nick@ubuntu:~$


nothing is happening at all. also i cannot edit the fstab file.

please any more help would be grateful

---

### Post by claets99 on 2006-04-09
i when i get properties of my drive - this is what happens.

[IMG]http://lemonbrook.com/sda%20properties.png[/IMG]

i cannot do anything on su in terminal. im just confused.

---

### Post by aysiu on 2006-04-09
[QUOTE=claets99]
EDIT: I have tried to unmount but nothing is happening in the terminal.[/quote] This is normal. > i try typing in sudo fdisk -l nothing appears. This is **not** normal and suggests something is wrong with your groups or /etc/sudoers. Unfortunately, how to fix this is out of my scope of knowledge.

---

### Post by claets99 on 2006-04-09
Thanks for you thoughts aysiu. From what i can see, I just cannot access anything in the root. Now when the computer first had ubuntu install (earlier this morning) I could see my HDD's mounted to the desktop. So i went straight away to click on them and recieved the error about user permissions. It is possible to say, boot of DSL or knoppix, change some files that have the info about the users and get ubuntu to run staight into the root?

Like i said, ever since the first installation I cannot access the hard drives. Now i cant  even access the user groups or SPM. Would a new format fix this.

Btw I have a 250gb SATA drive with 3 ntfs partitions, a 512MB swap and 12.5 root for ubuntu.

---

### Post by Ramses de Norre on 2006-04-09
What's the output of groups? (type groups in terminal)
Can you do sudo su and type in your normal user passwd?

---

### Post by claets99 on 2006-04-09
when i type groups into terminal and i get the following

> nick@ubuntu:~$ groups
sudo


ive been loged on as root@ubuntu using the recover console and ive tried to change the mount order to the following > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs nls=utf8,umask=0222 0 0
/dev/sda5       /media/sda5     ntfs nls=utf8,umask=0222 0 0
/dev/sda6       /media/sda6     nntfs nls=utf8,umask=0222 0 0
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

is there like a linux version of a batch comand that i can run from my pen drive or CD?

---

### Post by Ramses de Norre on 2006-04-09
Is that the only user? Created by the installer? you have to be in the admin group to use sudo or do in recovery: vi /etc/sudoers 
Then change %admin  ALL=(ALL) ALL in %sudo  ALL=(ALL) ALL
Or add yourself to the admin group, but I don't remember the command to do that right away, it would be a better method in fact.

---

### Post by claets99 on 2006-04-09
Yeah Nick is the only user - but I cant get to the Users and Groups tab to access anything. The tab just wont load up. I will go into recovery and type in that command but how can I delete the fstab file and then copy a new stab file over to the /etc location? I mean theres i mean if i can get su access i will be able to view the drives, and also use other commands within the system.

---

### Post by claets99 on 2006-04-09
[QUOTE=Ramses de Norre]Is that the only user? Created by the installer? you have to be in the admin group to use sudo or do in recovery: vi /etc/sudoers 
Then change %admin  ALL=(ALL) ALL in %sudo  ALL=(ALL) ALL
Or add yourself to the admin group, but I don't remember the command to do that right away, it would be a better method in fact.[/QUOTE]
 
OK thank you all for your help. I have managed to sucessfully sort the problem. I did the last suggestion and edited the sudoers file from visudo in recovery console. Took me a long time to work it out but after when i logged in, i went back to User and Groups and selected all options from the properties of the name. I could then successfully unmount the drives. Then i followed advise from earlier, changed the fstab file (because i could now do that) to include the special ntfs nls=utf8,umask=0222 0 0 code on my drives, remount with sudo mount -a and voila...... the drives are back and i can access the contents. My next step is to edit and save to these partitions, which ive found you can do with some sort of external software. Anyways, im glad i fixed the problem and hope this will help people in the future.

---

### Post by Ramses de Norre on 2006-04-09
By default I was in a lot of groups to gain acces on certain things (like cdrom, 3d acceleration,...), this is the output of groups: ```
ramses adm dialout cdrom floppy tape audio dip video plugdev lpadmin scanner admin

```
So you can add yourself to these groups if they exist and if you add yourself to admin you can change your sudoers file back to the default too.

---

