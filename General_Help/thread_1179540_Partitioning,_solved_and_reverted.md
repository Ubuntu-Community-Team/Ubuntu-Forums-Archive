---
title: "Partitioning, solved and reverted"
date: 2009-06-05
forum: General Help
---

### Post by texas.chef94 on 2009-06-05
Through the help of this community I thought I had my partitioning problem solved.
I had 2 partitions and was having difficulty setting up 3rd
In terminal
sudo mkdir /storage
sudo gedit /etc/fstab
added
/dev/sdb3 /storage ext3 defaults 0 0
Saved
sudo mount -a
sudo chown -R allen:allen /storage
sudo chmod -R 755 /storage
Came back to Nautilus there it was clicked on it and added a file to be certain I was home free and it worked.
Booted today not there on nautilus

[http://s577.photobucket.com/albums/ss219/worthamtx/](http://s577.photobucket.com/albums/ss219/worthamtx/)

Screen Shot drive and I suspect its what I do not know about mnt points

Thanks as always

---

