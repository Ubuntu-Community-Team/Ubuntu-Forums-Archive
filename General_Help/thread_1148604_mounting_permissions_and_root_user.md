---
title: "mounting permissions and root user"
date: 2009-05-04
forum: General Help
---

### Post by kash959 on 2009-05-04
I just installed Ubuntu 9.04 recently and i must say i'm never going back to windows again ;)
I've got a couple of issues tho. I mounted a drive '/dev/sda3' in to /home/kash/stuff by using the following command.

sudo mount /dev/sda3 /home/kash/stuff

it mounted fine but the only problem is that i can't delete or add stuff to it unless i do it through the terminal using the sudo command. and also all the files have a lock image onto them so i tried to change the ownership and permissions but it won't let me.

also, i ended up unlocking the root but i don't know if that's a good idea. i want to lock it again like it was before. any ideas. thanks:popcorn:

the pop corn is for watching windows vista getting it's *** kicked by ubuntu lol

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> I just installed Ubuntu 9.04 recently and i must say i'm never going back to windows again ;)
I've got a couple of issues tho. I mounted a drive '/dev/sda3' in to /home/kash/stuff by using the following command.

sudo mount /dev/sda3 /home/kash/stuff

it mounted fine but the only problem is that i can't delete or add stuff to it unless i do it through the terminal using the sudo command. and also all the files have a lock image onto them so i tried to change the ownership and permissions but it won't let me.

also, i ended up unlocking the root but i don't know if that's a good idea. i want to lock it again like it was before. any ideas. thanks:popcorn:

the pop corn is for watching windows vista getting it's *** kicked by ubuntu lol

You mounted the drive using sudo, meaning root is owner of the drive.
You can change this using:
```
sudo chown -R kash:kash /home/kash/stuff
```
Also now you have to use sudo. The double kash stand for user:group.
The -R will also change ownership of files and folders in folder stuff.

---

### Post by kash959 on 2009-05-04
hmmm... it says : -

kash@Laptop:~$ sudo chown -R kash:kash /home/kash/stuff
chown: changing ownership of `/home/kash/stuff': Operation not permitted
kash@Laptop:~$

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> hmmm... it says : -

kash@Laptop:~$ sudo chown -R kash:kash /home/kash/stuff
chown: changing ownership of `/home/kash/stuff': Operation not permitted
kash@Laptop:~$

That's very strange. I would expect this to work. Can you do the following:
Open a terminal. It will open in your home folder: /home/kash
type
```
ls -l
```
Now it will show the contents of your home folder.
Select the complete line where stuff is listed and press ctrl-shift-c
(In terminal this the normal copy function)
Paste the line into your answer here.

---

### Post by kash959 on 2009-05-04
drwxr-xr-x 3 root root  16384 1970-01-01 01:00 stuff

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> drwxr-xr-x 3 root root  16384 1970-01-01 01:00 stuff

I don't expect this to change anything but why do you live in 1970? Is something wrong with your computer clock? Which date and time do other files and folders show?
Normally spoken the command I gave you should work, I have no idea why it doesn't. Maybe somebody else knows.

---

### Post by kash959 on 2009-05-04
lmfao.  i didn't even notice that. the clock on the desktop shows the time and date correctly.
no problem lol thanx for checkin it out

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> lmfao.  i didn't even notice that. the clock on the desktop shows the time and date correctly.
no problem lol thanx for checkin it out

As said before it should work but it didn't. Now I have no idea how to help you any further. Sorry.
I do think it is strange that the folder stuff has this strange date and time. Do other files and folders also have that?

Success.

---

### Post by kash959 on 2009-05-04
what the hell. they actually are all 2009 except this folder. i'm gona try and make a new folder and mount it there and see wat happens

---

### Post by kash959 on 2009-05-04
ok this is messed up. i deleted stuff and created a brand new folder called things. i did the command :-
ls -l

it showed the date to be 2009.
i mounted /dev/sda3 to that folder and the date for this brand new folder changed to 1970. why the hell could that be happening?!?! is my computer possessed :cry:

---

### Post by DGortze380 on 2009-05-04
> **kash959 said:**
> I just installed Ubuntu 9.04 recently and i must say i'm never going back to windows again ;)
I've got a couple of issues tho. I mounted a drive '/dev/sda3' in to /home/kash/stuff by using the following command.

sudo mount /dev/sda3 /home/kash/stuff

it mounted fine but the only problem is that i can't delete or add stuff to it unless i do it through the terminal using the sudo command. and also all the files have a lock image onto them so i tried to change the ownership and permissions but it won't let me.

also, i ended up unlocking the root but i don't know if that's a good idea. i want to lock it again like it was before. any ideas. thanks:popcorn:

the pop corn is for watching windows vista getting it's *** kicked by ubuntu lol

What format is the drive?

you probably want one of the following commands instead

FAT32
```

sudo mount -t vfat /dev/sda3 /home/kash/stuff

```

NTFS
```

sudo mount -t ntfs-3g /dev/sda3 /home/kash/stuff

```

---

### Post by DGortze380 on 2009-05-04
> **kash959 said:**
> 
i mounted /dev/sda3 to that folder and the date for this brand new folder changed to 1970. why the hell could that be happening?!?! is my computer possessed :cry:

It's likely a problem with the timestamps on the file system you are mounting.

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> ok this is messed up. i deleted stuff and created a brand new folder called things. i did the command :-
ls -l

it showed the date to be 2009.
i mounted /dev/sda3 to that folder and the date for this brand new folder changed to 1970. why the hell could that be happening?!?! is my computer possessed :cry:

I start to wonder if your initial mound command is correct.
Please type the following commands one by one in a terminal and copy paste the output in your answer please.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by kash959 on 2009-05-04
i tried the FAT32 command and it mounted. i am able to delete and do stuff with the 'things' folder but i can't create anything within it unless i copy it using 'sudo cp' command.
-------------------------------------------
kash@Laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb8a8fe4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         547     4393746   83  Linux
/dev/sda2             548         608      489982+   5  Extended
/dev/sda3             609       19457   151404592+   b  W95 FAT32
/dev/sda5             548         608      489951   82  Linux swap / Solaris
--------------------------------------------
kash@Laptop:~$ sudo blkid
/dev/sda1: UUID="1899bc5a-edf3-4882-a864-c49dce5dfa42" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="bd5dfa20-a365-4153-8bc7-69f4b2fdfb6c" 
/dev/sda3: UUID="44D7-4F7A" TYPE="vfat" 
--------------------------------------------
kash@Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1899bc5a-edf3-4882-a864-c49dce5dfa42 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bd5dfa20-a365-4153-8bc7-69f4b2fdfb6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-----------------------------------------------------------------------
kash@Laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.2G  3.7G  261M  94% /
tmpfs                 880M     0  880M   0% /lib/init/rw
varrun                880M  112K  880M   1% /var/run
varlock               880M     0  880M   0% /var/lock
udev                  880M  144K  880M   1% /dev
tmpfs                 880M  196K  880M   1% /dev/shm
lrm                   880M  2.4M  878M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda3             145G   13G  132G   9% /home/kash/stuff
/dev/sda3             145G   13G  132G   9% /home/kash/things
----------------------------------------------------------
hope all that make sense lol. i also want to ask what is this '/etc/fstab/' file all about because when i was googling about this it came up a few times

---

### Post by DeMus on 2009-05-04
> **kash959 said:**
> i tried the FAT32 command and it mounted. i am able to delete and do stuff with the 'things' folder but i can't create anything within it unless i copy it using 'sudo cp' command.
-------------------------------------------

Well, the fstab file keeps records of all mounted drives.
You never wrote sda3 is a fat drive. Well, I never asked so why should you?

Okay, now you have mounted it as a fat drive and it partly works.
I do expect now we have to start using the chown instruction again to make the sda3 drive your drive and not root's drive.
So, open a terminal and type:
```
sudo chown -R kash:kash /home/kash/things
```
or when this does not work you could try:
```
sudo chown -R kash:kash /dev/sda3
```
But I'm not sure this is a legal command. Can somebody else please help?

---

### Post by kash959 on 2009-05-04
i'm gona reformat the drive and start over.

---

### Post by kash959 on 2009-05-04
how do u remove a directory using 'rm' command. i did it using the browser but i jst wana know lol

---

### Post by kash959 on 2009-05-04
OMG why!!!
i deleted the partition and recreated it. deleted the folders 'stuff','things' and a couple of others.
recreated stuff and mounted /dev/sda3 to stuff.
i can delete the folder stuff but when i go into stuff, i can't create anthing. when i go into folder properties it says the owner is kash:kash and i can create or edit and stuff...
when i do
ls -l
it shows 'root root' whereas with others it shows 'kash kash'..
why?!?!?!?!?!?!?!?!? this is bull

---

### Post by kash959 on 2009-05-04
oh yea!! it seems to have worked. i just mounted it again and it's doing fine :)
thanx for helpin me. +rep.. idk if this forum offers rep lol

---

### Post by jesuspresley on 2009-05-04
Please, kash959, take some speed out of this. 
I successfully mounted my windows ntfs drive into my home folder, and it should be even easier with your FAT drive.... 

So I guess it's a question of sucessfully transalting the limited right management of FAT32 to the Linux world. 

Try to use the umask option:
```
mount -t vfat -o umask=000 /dev/sda3 /home/kash/things
```

[Source]("http://www.daniweb.com/forums/thread22358.html#")

Does this help?

Edit: I was too late...

---

