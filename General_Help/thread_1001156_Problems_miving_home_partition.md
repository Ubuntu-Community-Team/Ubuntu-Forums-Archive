---
title: "Problems miving home partition"
date: 2008-12-03
forum: General Help
---

### Post by josephmo on 2008-12-03
OS: Ubuntu 8.1 64 bit
Storage system:

One 250 GB hard drive /dev/sdba partitioend by Ubuntu during install

One 500 GB hard drive /dev/sdb installed later, and partitioned as NTFS.

username: joseph

After the initial install of Ubuntu, a home directory /home was created on /dev/sdba. I wanted to move the /home directory to the 500 GB drive. I asked on the Ubuntu forums, and did some additional research, and this is the procedure I followed:

#su
#root password (I entered the root password).
#mkdir /mnt/newhome
#sudo mount -t ntfs /dev/sdb1 /mnt/newhome
#cd /home/
#find . -depth -print0 | cpio --null --sparse -pvd /newhome/
#sudo umount /mnt/newhome
#sudo mv /home /old_home
#sudo mkdir /home
#sudo mount /dev/sdb1 /home

I then added the following line to the end of /etc/fstab:

/dev/sdb1 /home /ntfs nodev,nosuid 0 2

The I did this:

#sudo rm -rf /old_home

When I restarted the system, I did a login as joseph and entered my password. I then got some error message about /.dmrc and /.ICEauthority files.

I restarted the system into RECOVERY mode, logged in as root, and did the following:

#chown -R joseph:joseph /home/joseph
#chmod 644 /home/joseph/.dmrc
#chmod 644 /home/joseph/.ICEauthority

and restarted normally. This time after my login as joseph, I got the following message:

User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

If I click on OK, I am logged in fine. The HOME directory is now switched to the new hard disk (/dev/sdb1), and when I copied my users/joseph directory from my Vista system, into my new home directory, it copied fine. If I go into /home/joseph and do:

#ls -l -a .dmrc

I get the following:

-rwxrwxrwx 1 root root 28 2008-12-03 12:41 .dmrc

#ls -l -a .ICEauthority

I get the following:

-rwxrwxrwx 1 root root 2888 2008-12-03 13:26 .ICEauthority

Both files are showing root as owner, when I though that ownwership should be joseph. In fact, if I do cd /home/joseph and I do an:

#ls -l -a

The resulting listing shows all files and directories as owned by root.

Any ideas?

--thx, Joseph

---

### Post by taurus on 2008-12-03
Using ntfs filesystem (/dev/sdb1) for /home is a bad idea.  You will run into all kind of permissions problem if you have not already.  If you want to move /home to that 500GB harddrive, use ext3 filesystem.

---

### Post by josephmo on 2008-12-03
> **taurus said:**
> Using ntfs filesystem (/dev/sdb1) for /home is a bad idea.  You will run into all kind of permissions problem if you have not already.  If you want to move /home to that 500GB harddrive, use ext3 filesystem.

Consulting the Ubuntu documentation, it tells me that NTFS and ext3 have the same features under Linux. Having an NTFS file system on the separate drive, allows me to mix Vist and Linux machines without any problems as Vista cannot see ext3 drives.

---

### Post by caljohnsmith on 2008-12-03
The problem is that NTFS does not support ownership/permission metadata. :) If you want to move your entire home directory to its own partition, you should use a linux file system like ext3. Or you could keep your home directory in your root partition so that it has all the necessary ownership/permissions info, and then just move your personal Music, Documents, Videos, etc directories to your NTFS sdb1 partition; then you can then create a symbolic link to your personal folders on the NTFS partition back to your home directory. I know that works. Anyway, let me know how it goes or if you run into more problems.

EDIT: Ooops, I see while I was typing my answer Taurus all ready pointed out the NTFS problem.

---

### Post by josephmo on 2008-12-03
> **caljohnsmith said:**
> The problem is that NTFS does not support ownership/permission metadata. :) If you want to move your entire home directory to its own partition, you should use a linux file system like ext3. Or you could keep your home directory in your root partition so that it has all the necessary ownership/permissions info, and then just move your personal Music, Documents, Videos, etc directories to your NTFS sdb1 partition; then you can then create a symbolic link to your personal folders on the NTFS partition back to your home directory. I know that works. Anyway, let me know how it goes or if you run into more problems.

EDIT: Ooops, I see while I was typing my answer Taurus all ready pointed out the NTFS problem.

OK, so now I need to reverse this process, and move the home directory back to its original location (and where would that be? /dev/sda1?)? then reformat the extra hard drive as ext3, and then re-reverse the process?

---

### Post by caljohnsmith on 2008-12-03
> **josephmo said:**
> OK, so now I need to reverse this process, and move the home directory back to its original location (and where would that be? /dev/sda1?)? then reformat the extra hard drive as ext3, and then re-reverse the process?
Yes, that's probably the best way. While you have sdb1 mounted on /home, you could do:
```
sudo mkdir /home_backup
sudo cp -ax /home/* /home_backup
```
And then check to make sure the /home_backup folder has everything before you wipe the sdb1 partition and change it to ext3.

---

### Post by josephmo on 2008-12-03
> **caljohnsmith said:**
> Yes, that's probably the best way. While you have sdb1 mounted on /home, you could do:
```
sudo mkdir /home_backup
sudo cp -ax /home/* /home_backup
```
And then check to make sure the /home_backup folder has everything before you wipe the sdb1 partition and change it to ext3.

When I do:

sudo cp -ax /home/* /home_backup

I get this message:

cp: cannot stat `/home/joseph/.gvfs': Permission denied

everything else in the home directory seems to have copied OK

---

