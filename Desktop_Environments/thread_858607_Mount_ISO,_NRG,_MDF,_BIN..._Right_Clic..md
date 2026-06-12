---
title: "Mount ISO, NRG, MDF, BIN... Right Clic."
date: 2008-07-13
forum: Desktop Environments
---

### Post by dlzerocool on 2008-07-13
After few reads and tests of other softwares and nautilus scripts I decided to do one that I can use easily. Because I didn't liked the other ones.

Everything works with right clic on the file you want :
Scripts ->  Mount Unmount Convert

How to use :
Convert files .xxx in .iso  (Right clic -> scripts -> convert.sh)
Read the messages and that's all :)

You can now mount the new iso (Right clic -> scripts -> mount.sh or unmount.sh to unmount)

To install copy this in a terminal(console)
```
wget http://www.dlcideas.com/linkimages/mountiso_gnome.sh
chmod +x mountiso_gnome.sh
./mountiso_gnome.sh

```
I hope this will help some of you.
cya

---

### Post by dlzerocool on 2008-07-15
For people who had problem with this script:

please delete the directory  /home/youruser/tmp 

```
sudo rm -R ~/tmp

```

The new version is correct, the old one had wrong files names.

Sorry. Now it works try again :)

---

### Post by Happless on 2008-07-18
Again, thanks so much for this script. It has made many tedios chores dissappear.

---

### Post by dlzerocool on 2008-07-18
Thanks a lot for your comment.

I've also made a script UbuntuGamerz, perhaps you are interested in.
[http://ubuntuforums.org/showthread.php?t=859178&highlight=ubuntugamerz](http://ubuntuforums.org/showthread.php?t=859178&highlight=ubuntugamerz)

---

