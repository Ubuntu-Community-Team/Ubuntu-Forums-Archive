---
title: "Changing permissions of HFS+ from livecd"
date: 2009-04-16
forum: General Help
---

### Post by pmatos on 2009-04-16
Hi all, [using 8.04 livecd]

I have read :
[http://ubuntuforums.org/showthread.php?t=123785](http://ubuntuforums.org/showthread.php?t=123785)

and tried to reply there but for some reason the forums software didn't allow me to post there.

I have a corrupted HFS+ that macbook doesn't boot. But Ubuntu is able to mount it. If, however I try to copy it...  it fails saying that the owner of some dirs is 501 and it can't copy anything because the dir is read-only. 
I can't change the rights even though in /etc/mtab it says the partition is mounted as rw.

How can I change the permissions in it? Unfortunately gparted says it's not able to check/repair the partition. 

Any suggestion?

Cheers,

Paulo Matos

---

### Post by StuartN on 2009-04-16
You can change the ownership of files with chown user:group file, for instance chown stuart:stuart temp.txt would give me ownership of temp.txt (stuart belongs to group stuart in a standard Ubuntu installation). sudo chown root:root temp.txt would give the file to root. sudo chown bill:bill -R testdir would recursively change the ownership of testdir and all directories/files in it to bill. ls -l will show the owner.

Permissions can be changed with ug+=rw to add read and write permission for user and group, or uga+=rw to include all. For instance sudo chmod ug+=rw -R testdir will recursively add read and write permission to testdir and all files in it for their owner and group.

---

### Post by pmatos on 2009-04-16
> **StuartN said:**
> You can change the ownership of files with chown user:group file, for instance chown stuart:stuart temp.txt would give me ownership of temp.txt (stuart belongs to group stuart in a standard Ubuntu installation). sudo chown root:root temp.txt would give the file to root. sudo chown bill:bill -R testdir would recursively change the ownership of testdir and all directories/files in it to bill. ls -l will show the owner.

Permissions can be changed with ug+=rw to add read and write permission for user and group, or uga+=rw to include all. For instance sudo chmod ug+=rw -R testdir will recursively add read and write permission to testdir and all files in it for their owner and group.

Thank you but I already know that. The problem is that the partition is ro.

---

### Post by StuartN on 2009-04-16
If you don't mind the risk then you could try mount -w -s, where the -s (sloppy) ignores filing system errors. The safest option would be to put the drive in an external caddy and fix it with a Mac.

---

### Post by pmatos on 2009-04-16
> **StuartN said:**
> If you don't mind the risk then you could try mount -w -s, where the -s (sloppy) ignores filing system errors. The safest option would be to put the drive in an external caddy and fix it with a Mac.

Don't have external caddy but have several external disks. Can I use livecd to 'clone' the drive into a bigger sized external drive? Maybe with dd?

---

### Post by StuartN on 2009-04-16
> **pmatos said:**
> Don't have external caddy but have several external disks. Can I use livecd to 'clone' the drive into a bigger sized external drive? Maybe with dd?

I would not try to clone a faulty partition. It would be best to back up whatever data is retrievable or to fix the partition using a native Mac utility, if you can get it connected to a functioning Mac.

However this thread does give instructions to compile Darwin utilities and fix hfs+ under Linux: [http://ubuntuforums.org/showthread.php?p=2346494](http://ubuntuforums.org/showthread.php?p=2346494)

---

### Post by coffeecat on 2009-04-16
**pmatos,** I don't know why mtab is saying that your hfs+ partition is mounted rw because with the kernel that came with 8.04, hfs+ filesystems can only be read, not written to. I don't know whether hfs+ write drivers have been incorporated into later kernels, but that won't affect you if you are using 8.04. And you don't want to be using gparted or any other Linux utility to repair the filesystem - even if you could. If an Apple Mac can't do it, nothing will. In the circumstances, you're lucky to be able to read it in Linux, so it would be a good idea to copy any valuable data off it as soon as possible.

Because you can't write you can't change permissions. That 501 is the default UID that MacOS uses for the first created user. Ubuntu uses a UID of 1000, both MacOS and Ubuntu/Linux using the same Unix permissions system. If, because of the differing UIDs, you encounter problems navigating into sub-folders in order to copy off data, then you'll have to invoke root powers with 'sudo cp' from the terminal, or 'gksudo nautilus' to get a root nautilus. Then, if you copy to a Linux filesystem, you'll have to sudo chown everything to your ownership.

Or, better still, copy to a NTFS filesystem. This is the one occasion where the inadequacies of Microsoft filesystems are an advantage - they don't support Unix permissions - so you won't run into permissions problems with the copies if you copy hfs+ -> ntfs.

And I agree with the last poster. Don't clone from a faulty filesystem. Simply copy what you need.

---

### Post by pmatos on 2009-04-17
> **coffeecat said:**
> **pmatos,** I don't know why mtab is saying that your hfs+ partition is mounted rw because with the kernel that came with 8.04, hfs+ filesystems can only be read, not written to. I don't know whether hfs+ write drivers have been incorporated into later kernels, but that won't affect you if you are using 8.04. And you don't want to be using gparted or any other Linux utility to repair the filesystem - even if you could. If an Apple Mac can't do it, nothing will. In the circumstances, you're lucky to be able to read it in Linux, so it would be a good idea to copy any valuable data off it as soon as possible.

Because you can't write you can't change permissions. That 501 is the default UID that MacOS uses for the first created user. Ubuntu uses a UID of 1000, both MacOS and Ubuntu/Linux using the same Unix permissions system. If, because of the differing UIDs, you encounter problems navigating into sub-folders in order to copy off data, then you'll have to invoke root powers with 'sudo cp' from the terminal, or 'gksudo nautilus' to get a root nautilus. Then, if you copy to a Linux filesystem, you'll have to sudo chown everything to your ownership.

Or, better still, copy to a NTFS filesystem. This is the one occasion where the inadequacies of Microsoft filesystems are an advantage - they don't support Unix permissions - so you won't run into permissions problems with the copies if you copy hfs+ -> ntfs.

And I agree with the last poster. Don't clone from a faulty filesystem. Simply copy what you need.

Thank you... I had just forgotten that ubuntu livecd default user doesn't give me root permissions. :) Obviously using sudo cp... works! :)

---

