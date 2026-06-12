---
title: "Partition problem......"
date: 2009-03-16
forum: General Help
---

### Post by LPHANTOM on 2009-03-16
Hi to all, I'm new on all the world of Linux and i have to many questions i hope you guys can help me out, I have a dell m1330 and I remove the original vista and install Ubuntu 8.10, I'm very happy with it, my problem it's that I have a 250gb hdd and i create a new partition of 200gb (ext3) just in case that I have to re-install Ubuntu, keep all my files on the 200gb partition, the think it's when I try to copy any files to the partition it show a window saying that I does no have permission to access  to the content and also show a folder called "Lost+Found" what this meas??? 

Thanks

---

### Post by taurus on 2009-03-16
Where do you mount that 200GB partition?  You just need to change the ownership of that mount point from root to your login name so you can write to it anytime you want.  

For now, I will _assume_ the mount point is /media/storage and your login name is tom, do

```
sudo chown -R tom:tom /media/storage
touch /media/storage/testing
ls -la /media/storage
```
You should see the new file, testing, with tom as the owner from the output of the last command.

To remove it, just run

```
rm /media/storage/testing
ls -la /media/storage
```

---

### Post by LPHANTOM on 2009-03-16
wow that was very helpful, thank a lot. Now in that partition I want to place all my music, documents, etc.... and I already create the folders, my question is, its any way to redirect the short cut on places to the new ones or should I have to access to the new partition every time that I want to check my files? Thanks and my best Regards

---

### Post by taurus on 2009-03-16
Assuming you have /media/storage/music, /media/storage/movies, /media/storage/documents, /media/storage/backup, you can link them to your $HOME.

```
ln -s /media/storage/music ~/music
ln -s /media/storage/movies ~/movies
ln -s /media/storage/documents ~/documents
ln -s /media/storage/backup ~/backup
```

So want you save files to music in your $HOME, ~/music, they would automatically be saved to /media/storage/music.

---

