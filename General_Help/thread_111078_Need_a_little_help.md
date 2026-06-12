---
title: "Need a little help"
date: 2006-01-01
forum: General Help
---

### Post by RoninGurl on 2006-01-01
I have been using the Ubuntu Live CDs for quite some time now and gone through several of your releases and the Breezy Badger 5.10 release is the first one to give me native support for my Linksys WLAN card so I am at this point ready to setup a dual boot system. However, I want to use the Windows XP boot manager where it shows the list of operating systems like I've seen on computers with both Windows 2000 and Windows XP Pro installed. I would like to add "Ubuntu Linux 5.10 (Breezy Badger)" to that boot list and be able to select it. 

The two operating systems would be installed on the same hard drive as I use my two other hard drives strictly for storage of files I want stored. No OS related files are on those, and it needs to stay that way. I started the Ubuntu installer to install it and when I got to the partitioning screen it really scared me. I've installed Red Hat before and it's installer was much more concise and well explained when it came to partitioning. I'd like to just get a list of directions I can use to make a 5 gigabyte partition for the Ubuntu install and leave Windows XP entirely to its own devices.

I browsed the forums a bit and found some topics on this but everyone seemed to be using different physical hard drives for each OS. I know it’s possible to do it my way since Red hat did it fine like a year ago (that setup no longer exists) but the Ubuntu installer is pretty confusing for the partition setups. Any help is greatly appreciated.

Thank you ahead of time.

---

### Post by RoninGurl on 2006-01-01
Oh and once Ubuntu is installed. How can I access my NTFS partitions? Even if only for read-only access. I'd like to be able to access my files on the Linux side of the OS game. For me FAT-32 is not an option because I like the features NTFS provides much like EXT3.

---

### Post by mcduck on 2006-01-01
I'd suggest that you reconsider using Grub instead of Windows bootloader, it would be much easier to set up..

Anyway, here's a nice web page with step-by-step instructions on dualbooting Ubuntu with windows, including pictures from the setup: [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

If you wish to resize a windows partition to make room for Ubuntu, boot win to safe mode first and run defrag. That way you'll have more continuous empty space in your disk and Ubuntu's installer can do the resizing :)

edit: here's a guide to mounting the NTFS partitions automaticly (in read-only mode): [http://makuchaku.info/amnesty/#automountntfs]("http://makuchaku.info/amnesty/#automountntfs")

---

### Post by RoninGurl on 2006-01-01
mcduck, That seems a little overly hard still. 
Could I resize with the red hat installer and then tell Ubuntu to use those partitions?

---

### Post by qferret on 2006-01-01
You can resize the partition with whatever utility your little heart desires. Resizing an NTFS partition with linux based tools can get a little tricky sometimes though....

---

### Post by RoninGurl on 2006-01-01
[QUOTE=qferret]You can resize the partition with whatever utility your little heart desires. Resizing an NTFS partition with linux based tools can get a little tricky sometimes though....[/QUOTE]
How tricky? I don't want to purchase Partition Magic or anything.
And assuming I do. How do I tell Ubuntu installer to use them?

And assuming the install goes badly. How do I tell the NTFS partition to reclaim the space.

---

### Post by qferret on 2006-01-01
Everything you want to know and more....
(FAQ and tutorial)

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

---

### Post by RoninGurl on 2006-01-01
God. You know what. I'm just going to do what I always did before. Ghost the C:/ drive before I do it. And restore the Ghost image as soon as the Linux breaks my C:/ drive. I did not want to do this but you guys are not making this sound like it is very reliable and I was hoping things would have matured in two years but I guess they haven't.

Hopefully in 30 minutes I'll be online again, except on Ubuntu 5.10.

---

### Post by Lord Illidan on 2006-01-01
Before you resize : defragment.

I have resized NTFS and FAT partitions and I haven't lost any data to the best of my knowledge. 2 tips.

1. Don't overdo it. Leave at least 1 gig free.
2. Make sure everything has been entered correctly BEFORE you press OK.

---

### Post by Lord Illidan on 2006-01-01
[quote=RoninGurl]God. You know what. I'm just going to do what I always did before. Ghost the C:/ drive before I do it. And restore the Ghost image as soon as the Linux breaks my C:/ drive. I did not want to do this but you guys are not making this sound like it is very reliable and I was hoping things would have matured in two years but I guess they haven't..[/quote]

Things have matured.. It is the best we can do, considering that NTFS is a closed source filesystem. However, it is a good precaution, and no, Linux won't break your C: drive, it is you who will break if it you do something wrong. I have installed different distros multiple times on 2 harddisks, even on the same harddisk with XP and nothing has gone wrong. Just take it easy.

---

### Post by RoninGurl on 2006-01-01
Here I am on Ubuntu 5.10 Breezy Badger.
It worked. Thanks folks. Just needed to Ghost drive first.

Now I need to get the NTFS drives to appear so I can listen to music.

---

### Post by qferret on 2006-01-01
Run:

sudo mkdir /mnt/ntfs

sudo nano /etc/fstab 

add the following to the end:

 /dev/<ntfs_partition> /mnt/ntfs ntfs users,owner,ro,umask=000 0 0

(replace <ntfs_partition> with the actual entry in /dev that corresponds to the appropriate partition)

Run:

mount -a

This will mount the partition for you. It will automount on subsequent boots.

---

### Post by qferret on 2006-01-01
btw.... congrats on the successful resize & install.  ;-)

---

