---
title: "problem changing permissions"
date: 2005-12-09
forum: General Help
---

### Post by damnhappy on 2005-12-09
For some reason I can't change the permisions for a folder. I have tried to change it using chmod and through logging in as root and checking the read/write/execute check boxes. Each time I check "write" it unchecks itself!
I have doen this before with no problems. Am I forgetting something stupid? 
just for refference this is the command I used to try and change the permission for this folder:
sudo chmod 777 /media/hdd1/mp3

It asks for my password, I enter it, but when I chek it only the read and execute privlages are enabled. :mad:

---

### Post by taurus on 2005-12-09
Does that mount automatically?  Perhaps you should look in /etc/fstab...

---

### Post by ninotob on 2005-12-09
That is odd -- the only thing that comes to mind is that it might be mounted read only which would probably interfere with setting it as writeable.

if you type ....

cat /etc/fstab

.... you can see the settings for your drive.  On the line where you see hdd1, if you also see "ro" that means it is being mounted as read only.  It's been a long time since I had to mess w/ fstab so if this is your issue, you should google for an fstab howto.

---

### Post by damnhappy on 2005-12-10
Hi Thanks for the help. I tried the cat /etc/fstab and there was no ro. 

I did figure it out though, at least how to change it, not why it happened. 
I unmounted the drive then remounted it manually as per the Unofficial Ubuntu Guide:
sudo mount /dev/hdd1 /media/hdd1/ -t vfat -o iocharset=utf8,umask=000

and it worked. The drive itself was read/write/execute for root, read/execute for  group and others, but all the subfolders were 777. I rebooted and the drive mounted automatically and the permissions were the same. :) 

Still a little worried about how it happened...:confused:

---

### Post by ninotob on 2005-12-10
I don't know why it happened but I'll take a guess -- it obviously isn't a linux filesystem (-t vfat so it is from MS).  It's safer to mount foreign drives read only so that the data is retreivable but not damageable.  For example, last time I checked (about a year ago) NTFS could be read reliably in linux, but writing was not stable ... that may have changed in the interim, but imagine how much damage a foreign drive could suffer if it was automatically mounted as read/write.  There would be much outcry on these boards to say the least.  No problem w/ writing to vfat though so this reasoning doesn't completely hold up.  Still, as I said, just a guess.

EDIT:  just noticed this thread right on the front page, NTFS still sketchy:
[http://www.ubuntuforums.org/showthread.php?t=100318](http://www.ubuntuforums.org/showthread.php?t=100318)

---

