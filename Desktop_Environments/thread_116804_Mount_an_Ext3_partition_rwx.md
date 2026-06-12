---
title: "Mount an Ext3 partition rwx?"
date: 2006-01-13
forum: Desktop Environments
---

### Post by r!ots on 2006-01-13
Hi.
i'm dual booting w2k and ubuntu.
for file sharing between these OS's i set up a 145GB ext3 partition (/dev/hdb3). with w2k everything works fine. after installing some ext2-drivers (ext2ifs) i now have read/write access onto the partition.
the problem i have is that i can't get ubuntu to mount the ext3-partition with all permissions for all users. somehow i can't figure out the mount options i have to list in the /etc/fstab-file. i thought umask would do it but it didn't. any suggestions on how to solve my problem?
many thx in advance.

my fstab looks like this:

proc            /proc           proc    defaults        0       0
/dev/hdb1       none            swap    sw              0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hdb3       /SharedMedia    ext3    defaults        0       1**
/dev/hda1       /mnt/w2k        ntfs    ro,defaults,exec,gid=100,umask=0222 0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by hillbilly on 2006-01-13
Change 
/dev/hdb3 /SharedMedia ext3 defaults 0 1
to

/dev/hdb3 /SharedMedia ext3 rw,user,auto 0 0

Hmm..i am not sure what the 1 at the end of the line is required for. if i remember correctly it is something to enable dump of the entire partition. But that is okay for now.

Check out this modified fstab by typing 
> mount /SharedMedia
at the terminal and see if you get proper access.

---

### Post by aysiu on 2006-01-13
I think if it's a Linux partition, you can mount it with defaults and then chmod the whole thing. ```
sudo chmod -R 777 /SharedMedia
```

---

### Post by hillbilly on 2006-01-13
Oh yes it can be done like that. I have been looking at too many posts with NTFS :-< !! 
Yeah if its a linux partition, you certainly can do like what aysiu said !

---

### Post by r!ots on 2006-01-14
if i do it the way aysiu recommended, what will happen to files i add later, especially while running w2k? what permissions will they have?

the 1 at the end of the line is used to enable a filesystem check with fsck every time this partition is mounted. (man fstab -> fs_passno)


edit: changing the fstab entry to 

> /dev/hdb3 /SharedMedia ext3 rw,user,auto 0 0

doesn't work. it doesn't even give me read permissions. only write for root and execute for all users. so i guess chmod is the only way to go, isn't it?

---

### Post by GTvulse on 2006-01-14
[QUOTE=r!ots]

edit: changing the fstab entry to 



doesn't work. it doesn't even give me read permissions. only write for root and execute for all users. so i guess chmod is the only way to go, isn't it?[/QUOTE]

Do you want to read and write files as if the partitoin were part of your account file space? Change the owner in the partition **superblock**:
```

sudo chown your_account:your_group /dev/[hs]d[a-z][1-16]

```
Where [hs] is the disk type, [a-z] is the disk location in the chain and [1-16] is one of the 16 partitions allowed in a DOS style partition table. You can also change the actual access permissions on the device file.

Now, as udev does its little thing every time you boot up, the best place to do these changes is in fact editing the udev rules files in /etc/udev.d (but do read the manual pages before attempting to do it. Summary: create your own rules file, make sure it is executed **last**.

---

### Post by r!ots on 2006-01-31
i haven't had time to try out draduls suggestions until today but somehow it still doesn't work.

[QUOTE=dradul]Do you want to read and write files as if the partitoin were part of your account file space? Change the owner in the partition **superblock**:
```

sudo chown your_account:your_group /dev/[hs]d[a-z][1-16]

```
Where [hs] is the disk type, [a-z] is the disk location in the chain and [1-16] is one of the 16 partitions allowed in a DOS style partition table. You can also change the actual access permissions on the device file.[/QUOTE]

i did
```

sudo chown 1000:100 /dev/hdb3

```
and it didn't change anything. it is still owned by root. i also tried unmounting and then remounting it. any suggestions?

[QUOTE=dradul]Now, as udev does its little thing every time you boot up, the best place to do these changes is in fact editing the udev rules files in /etc/udev.d (but do read the manual pages before attempting to do it. Summary: create your own rules file, make sure it is executed **last**.[/QUOTE]

do i append the rule to an existing rules file or do i create a new one? can you give me some hints on how to formulate the rule correctly?
thx in advance.

---

### Post by aysiu on 2006-01-31
[QUOTE=r!ots]if i do it the way aysiu recommended, what will happen to files i add later, especially while running w2k? what permissions will they have?[/QUOTE] You're planning to access that data from Windows? If so, don't make it Ext3. FAT32 would be better to share between operating systems.

---

### Post by lol on 2006-01-31
What I understand is the following : you want to use an ext3 partition the same way you would use a FAT32 partition mounted with umask=000, right? Meaning that you want for ALL users to have a rwx access on all files on this partition, regardless of who created them or when. Am I correct?

If so, I believe that the solution lies in "acl". I am no expert with this, I just discovered it recently while looking for a way to achieve what I previously described.

Anyway, to be able to use acl, you have to:

1 - modify /etc/fstab and add the acl option on the partition you want.
ex: "/dev/sda7       /home/shared    ext3    defaults,acl    0       0"
don't forget to remount the partition for the change to take effect.

2 - install acl -> apt-get install acl

3 - set the appropriate acl using "setfacl"

Understanding how acl works is not that simple that I cannot explain it in just a few sentences with my bad english, but you should definitely have a look at the man page or search for a tutorial on google.

For starter, here is a link that is not too bad : [http://www.ids.org.au/main/tutorials/acl_howto.php](http://www.ids.org.au/main/tutorials/acl_howto.php)

But as aysiu said, if you plan to access the partition from windows, forget about ext3 and use FAT32 instead...

---

### Post by r!ots on 2006-01-31
[QUOTE=lol]What I understand is the following : you want to use an ext3 partition the same way you would use a FAT32 partition mounted with umask=000, right? Meaning that you want for ALL users to have a rwx access on all files on this partition, regardless of who created them or when. Am I correct?[/QUOTE]

yes you're correct. i either want to make the partition a "second home directory", so i can rwx everything, or i want it to be rwx-able by all users. since it isn't the partition ubuntu is installed to, i don't have to care about security issues or do i?

i think ext3 is the better filesystem compared to fat32 and with the ext2ifs-drivers i found i haven't encountered any problems with w2k yet. so i can't see why i should use fat32.

i don't understand why it's so hard to make that partition rwx-able for all users. i mean i'm only a linux beginner but there should be an easy and fast way.

[QUOTE=lol]If so, I believe that the solution lies in "acl". I am no expert with this, I just discovered it recently while looking for a way to achieve what I previously described.

Anyway, to be able to use acl, you have to:

1 - modify /etc/fstab and add the acl option on the partition you want.
ex: "/dev/sda7 /home/shared ext3 defaults,acl 0 0"
don't forget to remount the partition for the change to take effect.

2 - install acl -> apt-get install acl

3 - set the appropriate acl using "setfacl"[/QUOTE]

thx for your suggestion i will try it out later.

---

### Post by icarius on 2006-01-31
I dual boot but with a fat32 partition that is shared between windows and ubuntu, can you change it over? Umask works well in my experience with fat32.

---

### Post by lol on 2006-02-01
> i don't understand why it's so hard to make that partition rwx-able for all users. i mean i'm only a Linux beginner but there should be an easy and fast way.

The easy and fast way under Linux is with ACLs. As far as I know, there is no other alternative to achieve what you want.

The drawback of using an ext3 file system to share files with windows is that the ext2ifs driver probably doesn't handle ACLs and files created from windows will have the "normal" default permissions. This can easily be solved by a startup script that would recursively set the ACLs you want on all files when you boot Linux.
I can understand why this wouldn't be the solution you dreamed of, but I honestly cannot think of another way to do that (and Google seems to agree with me). It is not for fun that people usually use FAT32 partitions, but simply because it is the most convenient way (if not the only one) too easily and quickly share files between Linux and windows.

Of course, I could be mistaken, and if you ever find another solution, please let me know, I am interested.

---

### Post by r!ots on 2006-02-05
hey. i think i got it working. thx a lot.

could you explain to me how i write a startup script so the acl are set every time i boot linux?
i've never done any scripting before so i don't know anything about it.

thx again. you have given me some great advice. i'm so relieved i don't have to use fat32.

---

### Post by lol on 2006-02-06
1 - Simply create a new file with a text editor (vi, gedit, whatever...) that should look like this:
```

#!/bin/sh
echo -n "Updating ACLs on the shared partition... "
setfacl -R -whatever_options_you_want /path/to/the/shared/folder
echo "done."

```
The first line is needed, but you can remove those starting with 'echo' if you prefer. You can add as many commands as you want in a script like this.

2 - Save the file. The location doesn't really matter, but startup scripts are usually all in /etc/init.d (and let's say you call it 'acl').

3 - make the file executable:
```

chmod +x /etc/init.d/acl

```

4 - Create a link in the proper runlevel (default is 2):
```

ln -s /etc/init.d/acl /etc/rc2.d/S20acl

```

each 'rc?.d' folder contains links to the scripts that have to be run in each runlevel. In Debian, the default runlevel is 2, so unless you changed this, all you need to do in create a link in 'rc2.d'. The links should start by S or K, depending if the script should be run with the 'start' or 'stop' parameter, and the number specify the order in which the scripts are executed.

---

### Post by RAOF on 2006-02-06
[QUOTE=lol]...
The drawback of using an ext3 file system to share files with windows is that the ext2ifs driver probably doesn't handle ACLs and files created from windows will have the "normal" default permissions. This can easily be solved by a startup script that would recursively set the ACLs you want on all files when you boot Linux...[/QUOTE]
Isn't the default permission for ACLs inherited from the parent directory?  I haven't actually tried it (I will soon, once I get around to it ;)), but can't you set it up so that files without ACLs just inherit the parent directory's ACL?  That way you only need to set an ACL for the root of the partition/mount point, and all the files/folders under it get the permissions you want.

---

### Post by lol on 2006-02-06
> Isn't the default permission for ACLs inherited from the parent directory?

Well, yes, that's the way it is supposed to work (at least, this is the what I understand).

> but can't you set it up so that files without ACLs just inherit the parent directory's ACL

I am not sure about that, and unfortunately I don't have a Windows available to test it. I believe that a new file inherit it's ACL when you create it. It this is the case, then what happens when the file is created by a tool which doesn't support ACLs?

---

### Post by lol on 2006-02-06
ok, I just tried to create a file using samba...
Here is what I have when I create a file using samba:
-rwxrwxr--+
and what I obtain when I create it on the local host:
-rw-rw-r--+ (which is actually what I want)

So it seems that if you create a file with a tool which does not support ACLs, you have to fix that later...

---

### Post by pelle.k on 2006-02-06
If so, wouldn't it be easier to just chmod 777 everything in this partion at boot-up?
I must say, i've always wondered why there isn't a thing such as a umask option in ext2/3 and ResierFS..

---

### Post by lol on 2006-02-06
> If so, wouldn't it be easier to just chmod 777 everything in this partion at boot-up

Actually, no it wouldn't be the same. If you have several users on the same computer, they need to be able to easily share files as long as Linux is up and running. If you just chmod all the files at boot time, files created later from Linux would not have the correct permissions.

The startup script is only needed if files are created on the partition from Windows.

---

### Post by pelle.k on 2006-02-06
Yeah, you're right. I didn't think of that!
But you know you can make the folder which is the mount point, set with 777 permissions "sticky", so that everything created should inherit those permissions. But i have to say i don't know how well it works, in practice.
Maybe ACL is the way to go.

---

