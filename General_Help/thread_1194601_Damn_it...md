---
title: "Damn it.."
date: 2009-06-22
forum: General Help
---

### Post by magh-87 on 2009-06-22
This is a very frustrating problem that is beginning to really bother me. Last week I posted a thread about my [girlfriend's laptop]("http://ubuntuforums.org/showthread.php?t=1192128") and the hard drive permission issues it was causing me. A post from another thread gave me an idea so I created a user using the same username that was on the mac, along with the UID 501.

I just turned on the hard drive and saw that the first folder no longer was denying me access. However, all of the other folders are. I'm trying to get this transition done for her before she goes off and spends a year in Germany, and I know she would like to have all of her files back on her computer before that happens.

If anybody has any suggestions I could really use some help at this point, thanks.

---

### Post by geirha on 2009-06-22
Hit Alt+F2 and run ```
gksu nautilus
```
Do that twice so that you get two nautilus windows with root privileges. In one of those windows, go to the backup folder; should be somewhere under /media/

In the other window, go to the home folder, and start dragging the files over.

The files you copy this way will be owned by root, so once you're done, change the ownership to the correct user, either from nautilus (run as root) or with the following command in a terminal:
```
sudo chown -R $USER:$USER $HOME
```
It recursively (-R) sets the current user ($USER) as owner on all files in the current user's home folder ($HOME)

---

### Post by HermanAB on 2009-06-22
Uhmmm... lemme see, the file owner is wrong, maybe the command chown is what you need:

$ sudo chown -R girlfriend:girlfriend /home/girlfriend

---

### Post by magh-87 on 2009-06-22
> **geirha said:**
> Hit Alt+F2 and run ```
gksu nautilus
```
Do that twice so that you get two nautilus windows with root privileges. In one of those windows, go to the backup folder; should be somewhere under /media/

In the other window, go to the home folder, and start dragging the files over.

The files you copy this way will be owned by root, so once you're done, change the ownership to the correct user, either from nautilus (run as root) or with the following command in a terminal:
```
sudo chown -R $USER:$USER $HOME
```
It recursively (-R) sets the current user ($USER) as owner on all files in the current user's home folder ($HOME)

I'm transfering these from one external to another.. is this going to be an issue? At the moment I don't have enough space on my hard drive for her files so would I do something similar to :
$ sudo chown -R USER:USER /HOME/HDD NAME ?

Thanks for your responses so far!

---

### Post by magh-87 on 2009-06-22
New dilemma, I'm able to copy some of the files over but not all of them. For example, I'm trying to copy some documents from her desktop over and I get the error that the file cannot be handled because I do not have the permissions to read it, even though I'm in nautilus.

Do I need to be in the user I created for my gf or should my Admin user be able to manage what it hasn't been doing for the last while?

The files that she wants the most I still can't transfer over, primarily her music, videos and pictures.

---

### Post by geirha on 2009-06-23
Could you post the output of the following command run in a terminal (while the external drives are connected)? ```
mount
``` It will list all mounted filesystems, and what type of filesystems they are, etc..

If you are running as the other user, you'll need to do the copying between two nautilus windows run as root (i.e. gksu nautilus), and the chown command will be different.
```
sudo chown -R *username*:*username* /home/*username*
```
Where you replace all three occurances of *username* with your gf's username.

If you want your gf to own the files on the external drive you are copying to as well, you run the same command as above, but replacing /home/*username* with the path to the external drive, which will be something like *"/media/HDD Name"*. It depends on the filesystem on the external drive though, whether you can set permissions like that or not.

---

### Post by magh-87 on 2009-06-24
> **geirha said:**
> Could you post the output of the following command run in a terminal (while the external drives are connected)? ```
mount
``` It will list all mounted filesystems, and what type of filesystems they are, etc..

If you are running as the other user, you'll need to do the copying between two nautilus windows run as root (i.e. gksu nautilus), and the chown command will be different.
```
sudo chown -R *username*:*username* /home/*username*
```
Where you replace all three occurances of *username* with your gf's username.

If you want your gf to own the files on the external drive you are copying to as well, you run the same command as above, but replacing /home/*username* with the path to the external drive, which will be something like *"/media/HDD Name"*. It depends on the filesystem on the external drive though, whether you can set permissions like that or not.

```
desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/myuser/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=myuser)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8)
/dev/sdc2 on /media/Time Machine Backups type hfsplus (rw,nosuid,nodev,uhelper=hal)
desktop:~$ 
```


I am currently attempting to transfer over 41GB of data from one external to another. No notice of permissions has come up as of yet so if one does I will post it here.

---

### Post by magh-87 on 2009-06-26
I have used nautilus to transfer everything from the Time Machine to the FreeAgent hard drive. Everything appears to be working and permissions don't seem to be an issue on the new hard drive. It's just a matter of having her go through everything and confirm that nothing is missing.

Thanks for all the help, I appreciate it!

---

