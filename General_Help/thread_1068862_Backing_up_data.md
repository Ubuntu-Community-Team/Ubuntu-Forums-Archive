---
title: "Backing up data"
date: 2009-02-13
forum: General Help
---

### Post by roshanjose on 2009-02-13
I wanted to backup all my data before i can format my system

I used this tutorial

[http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html](http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html)


but when i try to write the backup file onto either on my desktop or on a 8GB pen drive...the backup never finishes the 1st stage...

that is it keeps showing the message that its preparing for backup...

but even after long hours the backup is not yet prepared....

my home directory which i am trying to backup is 16GB

---

### Post by jonobr on 2009-02-13
recommend you breakup your data into manangeable chunks.

Eg, into a few different folders.

Right click on the folder and then select create archive.

if your folder is music
by default it will create music.tar.gz
etc.

With all your information archived and compressed, your ready to copy.

If your other desktop is ubuntu, you can do a secure copy from one to the other,

from the desktop type
(assuming the primary machine containing the information is called machine2 or use its IP address and your copying the music archive

scp [email]username@<machine2>:~/music.tar.gz[/email] .

do this for your other files also.

If machine 1, the backup machine is windoze, you could use winscp to do the copy

---

### Post by roshanjose on 2009-02-14
i have 64 bit hardy heron....

i wanted to install the 32 bit...and i have only ubuntu as OS...

so are there any other solutions

---

### Post by jonobr on 2009-02-17
AFAIK Rsync should work with both flavors,

Unless of course you weren't talking to me:-)

---

### Post by theozzlives on 2009-02-17
It's easier to have your /home on it's own partition.

---

### Post by handy on 2009-02-18
This a great site, & here is an excellent tutorial on how to make a separate /home partition:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

