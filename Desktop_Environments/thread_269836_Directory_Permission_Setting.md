---
title: "Directory Permission Setting"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Jason_Hampson on 2006-10-02
I'm sure this is very simple...

This is a follow on from a thread I started about Samba access ([http://www.ubuntuforums.org/showthread.php?t=266501)](http://www.ubuntuforums.org/showthread.php?t=266501)). Basically there is one directory I can browse from my XP machine and the other I can't. The Samba config file has the same setting for both folders, but the 'ls -l' command shows they have different access permissions.

I can access '/home/public'
   drwxrwxrwx  4 root   root   4096 2006-09-28 15:20 public


but I can't access '/media/hdb1/Music'
   drwxrwx--- 93 root plugdev     32768 2006-09-25 16:16 Music

I've ran the command 'sudo chmod a+rw Music', but running ls shows the same permissions as before. Running 'sudo chmod a-rw Music', takes away the permissions:
   d--x--x--- 93 root plugdev     32768 2006-09-25 16:16 Music

so I know the command is selecting the directory, but I don't seem to be able to set the permissions for everyone else. 

Is this because it's on a fat32 hd?

Thanks for your assistance

---

### Post by Iowan on 2006-10-02
Check/compare the parent directories of both shares to see if subdirectories have "inherited" permissions (or lack thereof).
(I notice the "groups" of the two shares are different...)

---

### Post by Blutack on 2006-10-02
A fat32 hd will not allow attributes like ownership to be set...I found that out the hard way after restoring from a copy of my system I put on an external HD.  Samba permessions can be a pest.  Hope this helps.

---

### Post by Jason_Hampson on 2006-10-02
Can you not share a fat32 drive using samba then?

I logged into Ubuntu as root and went through the GUI to set the directory permissions. I could check the permission check boces for 'others', but they unchecked themselves after a split second.

I have a large hd on my dual booted machine; I want both the local OS's to see it (Ubuntu + Windows) and I want to make it accessable via Samba, so my laptop can also see it ](*,)

---

### Post by dannyboy79 on 2006-10-02
well, in your fstab you have to specify the uid and the gid for your fat32 partition. i have 2 500gb hard drives formatted fat32 in my ubuntu server and I can access it just fine thru xubuntu as well as winxp using samba. i am not at home right now to show you my fstab entry but I will certainly post it when i get home. normally i could ssh into my machine from my work and get this kind of info but there was a huge storm last night (milwaukee, wi) and I turned my box off just in case.

---

### Post by dannyboy79 on 2006-10-02
nevermind, a simple google found the answer. Gogle is your FRIEND!!!!
i copied and pasted straight from a website so if the wording is funny that's why.
Editing your fstab file
Now that we see that things are working we can add an entry into the fstab file, doing so means that the filesystem will automatically be mounted on boot. Open the file /etc/fstab ( as root ) with your text editor and add the following line to the end of the file on a new line of it's own, also make sure it's all on one line. 

/dev/hda2  /mnt/fat  vfat  auto,rw,uid=0,gid=500,showexec,quiet,fmask=117,dmask=007  0  0
fstab options
The fstab line can be summarised as follows:

/dev/hda2 - This entry should be replaced by your device name from the fdisk output. 
/mnt/fat - This entry is the path to your desired mount point, /mnt/fat in my case. 
vfat - This is filesystem to mount, we could leave this as 'auto' for Linux to work it out for itself, but we know it's vfat so enter that. 
auto - This tells linux to mount the filesystem on boot. 
rw - Read/write access, could also be ro for read only 
uid=0 - User id of the owner of the filesystem mounted, uid=0 is roots uid, this is also the default 
gid=500 - Group id of the filesystem, you should add your normal logged in user here. To find the group id of your user open a terminal and type: 
$ id bobpeersWhere username is replaced by your actual username. This returns something like: 
$ uid=500(bobpeers) gid=500(bobpeers) groups=500(bobpeers)This gives you your uid and gid. Note that by default Fedora adds new users to their own group starting at 500, hence uid and gid are both 500. If I add another user then the uid and gid for that user will be 501. If you wish to also own the filesystem then set uid to this number in place of uid=0 from above. 
showexec - All windows executables ( .exe .com etc ) files are made executable ( permissions 770 ). 
quiet - the system will not output errors when we try to change file settings not supported by fat filesystems 
fmask=117 - this sets permissions on files, works the opposite to normal, so 117 equates to 660. In practise the owner and group have read/write access ( with execute also on .exe and other windows executables ) while others have no access at all. 
dmask=007 - same as above but only for directories. 
One other option that is useful is 'user', if you just add the word 'user' into the options line then this mount point can be mounted by any user but only that user can then unmount it, if you add the word 'users' then anybody can mount and unmount it. 


i will point out though that my uid and gid are 1000 since that's the first users id in ubuntu. actually after looking at this, this isn't like what i have, i think i have a umask option and a dmask option, both set to read and write for everyone since I am on  secure lan. i'll still post my fstab when i get home for ya. 

shit, i'll try 1 more time, here is a great website explaining all your options for mounting vfat or fat partitions in linux

[http://my.opera.com/lounge/forums/topic.dml?id=83440](http://my.opera.com/lounge/forums/topic.dml?id=83440)

good luck

---

### Post by Jason_Hampson on 2006-10-02
Thank you

I followed the instructions you refernced.

I changed:
vfat    defaults,nls=utf8,umask=007,gid=46 0       1 

to:
vfat rw,user,noexec,noauto,dev,async 0 0

and I can now access the folder over the network. I've only got read access at the moment, but I'm sure I'll work it out after I've had chance to read it properly.


Cheers!! :D (a happy user)

---

### Post by dannyboy79 on 2006-10-02
here ya go, this is what'as in my fstab and I can read and write over samba using my winxp box, i just map network drive and I am set! 

/dev/hdb5	/home/daniel/ntfs	ntfs	ro,uid=1000,gid=1000,nls=utf8,umask=0222	0	0
/dev/hdb1	/home/daniel/fat32	vfat	rw,uid=1000,gid=1000,iocharset=utf8,umask=0000	0	0

---

