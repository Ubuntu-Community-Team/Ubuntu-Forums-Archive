---
title: "i have two hard drives, and i cant access my slave."
date: 2005-12-17
forum: Desktop Environments
---

### Post by brianfoster on 2005-12-17
dont know why? the only difference i can see is that my slave drive has no partition.

---

### Post by Kelpie on 2005-12-17
actually i am having this problem myself, though my slave drive was reformatted and used to put all my important items on there for when i switched to Hoary, but Hoary doesnt see that my slave drive exists and i dont know another way around that to access the files on it, as most of them are of my artwork and would be readable on here, but its been formatted using windows 98 se before i switched so i was wondering if that could be the problem but i would like to beable to get my stuff from there

---

### Post by Ocxic on 2005-12-17
if your slave drive is on the Primary ide connector-and set to Slave in a terminal type :

sudo mkdir /mnt/Slave
sudo mount /dev/hdb1 /mnt/Slave
ln -s /home/your_username/Desktop/

that should allow you to see your slave drive brainfoster.
as for you kelpie if you formated your slave drive, yourhave lost all of your data on that drive, sorry bud.

---

### Post by poptones on 2005-12-17
How well does the linux fsck work on fat partitions? With a fsck.vfat -al you might be able to recover a good bit of data from it even if it's been formatted. If it works you'll likely have to pore through megabytes of lost&found folders, but it's better than losing your stuff.

---

### Post by Taranis on 2005-12-17
where can i find the steps for seeing my ntfs drive.
I have 5.10 on hdb and the ntfs files i want to back up on are hba2.
I can't see them in the file manager, nor in console, however i can see it in /.dev 
i just can get to it to move them.
i'm a nOOb, 

Thanks for any help!

---

### Post by aysiu on 2005-12-17
[QUOTE=Taranis]where can i find the steps for seeing my ntfs drive.
I have 5.10 on hdb and the ntfs files i want to back up on are hba2.
I can't see them in the file manager, nor in console, however i can see it in /.dev 
i just can get to it to move them.
i'm a nOOb, 

Thanks for any help![/QUOTE] See the fourth link in my sig.

---

### Post by brianfoster on 2005-12-17
[QUOTE=Ocxic]if your slave drive is on the Primary ide connector-and set to Slave in a terminal type :

sudo mkdir /mnt/Slave
sudo mount /dev/hdb1 /mnt/Slave
ln -s /home/brian/Desktop/

that should allow you to see your slave drive brianfoster.[/QUOTE]

this is when i hand typed it:

brian@BRILLIANTSTUDIO:~$ sudo mkdir/mnt/Slave
sudo: mkdir/mnt/Slave: command not found
brian@BRILLIANTSTUDIO:~$ sudo mount /dev/hdb1/mnt/slave
mount: can't find /dev/hdb1/mnt/slave in /etc/fstab or /etc/mtab
brian@BRILLIANTSTUDIO:~$ In -s /home/brian/desktop
bash: In: command not found
brian@BRILLIANTSTUDIO:~$

this is when i copied it into the terminal:

brian@BRILLIANTSTUDIO:~$
brian@BRILLIANTSTUDIO:~$ sudo mkdir /mnt/Slave
mkdir: cannot create directory `/mnt/Slave': File exists
brian@BRILLIANTSTUDIO:~$ sudo mount /dev/hdb1 /mnt/Slave
mount: you must specify the filesystem type
brian@BRILLIANTSTUDIO:~$ ln -s /home/brian/Desktop/
ln: `./Desktop': cannot overwrite directory
brian@BRILLIANTSTUDIO:~$

maybe that gives you a bit more info, thanks for helping.

---

### Post by Ocxic on 2005-12-19
ok sorry it should be 
"ln -s /home/brian/Desktop/Slave" not /home/brian/desktop/"

the mount point /mnt/Slave is alreasy there, thats ok.
What kind of file system is on the slave drive? after i know that i will give you the exact command.

---

### Post by tipi on 2005-12-19
is there anyway to get the disk mounted at startup
so you don't have to do this everytime?

---

### Post by dcstar on 2005-12-19
[QUOTE=tipi]is there anyway to get the disk mounted at startup
so you don't have to do this everytime?[/QUOTE]
Look at your /etc/fstab file, and add in another entry to suit.

---

### Post by LadyLuck on 2005-12-19
This was a useful thread for me. Thanx all. Now that I have hdb1 mounted under mnt/Slave why is it i cannot get acces to look at its content. The Slave should contain remnants of an NTFS file system

Incidentally on my road to this point I tried the "command" 

ls dev

(yes not "ls -dev") which gives me a long listing. Presumably possible devices and mounted devices? There is no expl. in "man ls." And while on the subject of "man pages" the commands "ls -a" and "ls -al" work as I am used to from my limited unix experience but "ls -d" gives only a rinki dink "-"

Cheers
LL ;)

---

### Post by Ocxic on 2005-12-19
this is my fstab entry for my NTFS harddisk, now you won't be able to write to the drive but you can read it. just modify it for your system

/dev/hdc1       /media/hdc1     ntfs    defaults,umask=0222        0       0

/dev/hdc1 is the disk to be mounted
/media/hdc1 is the mount point

leave everything else, just add it to the end of the file

---

