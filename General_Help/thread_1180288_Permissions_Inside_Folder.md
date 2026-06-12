---
title: "Permissions Inside Folder"
date: 2009-06-06
forum: General Help
---

### Post by joezamboni on 2009-06-06
chmod "123"

---

### Post by markharding557 on 2009-06-06
not sure there is not if you want all to be able to read them

---

### Post by tmo79 on 2009-06-06
I used the following to Backup my system Ubuntu 9.04

cd / 
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

It created a backup.tgz in the file system folder, durring the backup my HDD ran out of space.  At the end of that I tried to Cut and Paste the file on an enternal HDD, but because it was created i nthe file system folder I am unable to edit the file (read/write) I read a post advising to use the command "gksudo nautilus" when I did that I was able to"move to trash"  I moved it to trash but the 40GB did not free up on the system, nor was I able to access the Trash folder.  How can I find the file now? and how can II delete it or Move it?

Any advice? I am a Ubuntu noob :P  Thanks

---

### Post by michy99 on 2009-06-06
> **tmo79 said:**
> I used the following to Backup my system Ubuntu 9.04

cd / 
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

It created a backup.tgz in the file system folder, durring the backup my HDD ran out of space.  At the end of that I tried to Cut and Paste the file on an enternal HDD, but because it was created i nthe file system folder I am unable to edit the file (read/write) I read a post advising to use the command "gksudo nautilus" when I did that I was able to"move to trash"  I moved it to trash but the 40GB did not free up on the system, nor was I able to access the Trash folder.  How can I find the file now? and how can II delete it or Move it?

Any advice? I am a Ubuntu noob :P  Thanks

First of all, you should have started a new topic instead of hijacking this one.

Second, the files you deleted as root are in root's trash. To get rid of them, open a terminal and enter this command```
sudo rm -r /root/.local/share/Trash
```

---

### Post by michy99 on 2009-06-06
> **joezamboni said:**
> I have created a folder "/home/share" that all users can access. It works and anyone can create files and folders inside it. 

The one problem I have is that when someone creates a file in it, they are set to be the owner (so nobody else can read it).

I know it is possible to create a startup script that sets the permissions back to 777(I know its unsafe). So I want to know if there is a better way.
 
What is the output of```
ls -ld /home/share
```

---

### Post by tmo79 on 2009-06-06
Thanks a lot, I created a new thread for this but it was to late. Thanks

---

### Post by colau on 2009-06-06
> **tmo79 said:**
> I used the following to Backup my system Ubuntu 9.04

cd / 
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

It created a backup.tgz in the file system folder, durring the backup my HDD ran out of space.  At the end of that I tried to Cut and Paste the file on an enternal HDD, but because it was created i nthe file system folder I am unable to edit the file (read/write) I read a post advising to use the command "gksudo nautilus" when I did that I was able to"move to trash"  I moved it to trash but the 40GB did not free up on the system, nor was I able to access the Trash folder.  How can I find the file now? and how can II delete it or Move it?

Any advice? I am a Ubuntu noob :P  Thanks

That was really out of this thread.:D

---

