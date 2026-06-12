---
title: "Moving home to its own partition (on another drive)"
date: 2009-05-11
forum: General Help
---

### Post by texas.chef94 on 2009-05-11
My 9.04 is installed on my HD with nothing else.
I have had horrible luck creating a partition and moving home to it. Error 15 twice. So someone tell me is it possible to move home to my data drive which is huge ext4 with no OS installed there.
If it is please direct me to a tutorial if possible other then
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
Thanks so much 

Allen

---

### Post by logos34 on 2009-05-11
Try the link in my signature below. (I think this is the simplest).

Here's [another]("https://help.ubuntu.com/community/Partitioning/Home/Moving") using rsync.

(Note the part about '.gvfs' error.  Nothing to get worried about)

good luck

---

### Post by texas.chef94 on 2009-05-11
Got this far
Some folks even me can mess up a free lunch. That is me
[email]allen@allen-desktop:/home.bak[/email]/allen$ sudo mount -t ext4 /dev/sdb2 home
mount: mount point home does not exist
[email]allen@allen-desktop:/home.bak[/email]/allen$ 

What am I not doing correctly. Oh I did ext4 on home because that is what my data partition is in on same drive

Allen

---

### Post by rbc on 2009-05-11
I believe you need a slash in front of the word "home". In other words, the command should be:
sudo mount -t ext4 /dev/sdb2 /home

Also, if i am reading the instructions correctly, you should be doing as root, not just sudo

---

### Post by texas.chef94 on 2009-05-11
Well I amin real mess now. I know its me, but this is the one function that gives me more headaches then anything.
I am on other computer as I cannot boot.
Error message 
Your home directory is listes as /home/allen but it does not appear to exist. Do you want to log in with /(root) directory as your home directory?
Please advise in detail. Get me out and I will not try this again.

Allen

---

### Post by logos34 on 2009-05-11
boot the ubuntu live cd, mount your / partition, and reverse what you did:

**sudo mkdir /media/sda1 **(replace 'sda1' with your root)

**sudo mount -t ext3 /dev/sda1 /media/sda1 **(or maybe it's ext4)

- remove the empty 'home' directory and rename your 'home.bak' back to 'home'

**sudo mv /media/sda1/home.bak /media/sda1/home**

MAKE SURE YOU DELETE THE EMPTY HOME AND NOT THE ORIGINAL

**sudo umount /media/sda1**

exit the live cd session and reboot into 9.04 jaunty

hopefully back to original state.

*ADD: I'm assuming from the info you gave that you didn't cp the contents of /home to sdb2.  And/or maybe you didn't edit fstab (whence the error)?

---

### Post by texas.chef94 on 2009-05-12
Thank  you. I guess some of us has to have a stumbling block and mine is home to its own partition. I appreciate your help

Allen

---

### Post by logos34 on 2009-05-12
Here's the only other [guide ]("http://www.psychocats.net/ubuntu/separatehome")for making a separate /home I know of.  It's quite popular.  Maybe it will help you understand where you went wrong. (the actual commands are very similar).

enjoy ubuntu

---

### Post by texas.chef94 on 2009-05-12
Thanks to all, but this one gets me in trouble evey time  so I am back to normal and will stay there.

Allen

---

