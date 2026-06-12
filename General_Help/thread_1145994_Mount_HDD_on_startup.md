---
title: "Mount HDD on startup?"
date: 2009-05-02
forum: General Help
---

### Post by toejamfootball on 2009-05-02
Hi, I followed this HOWTO [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

I did this twice (because the first time, I wasn't expecting it to do what it did), so now the drive mounts in two different places.

I would like to just have it mounted in one place, how can I do this?

Also, is it possible to have it show up on the Desktop as a HDD, rather than just a Folder inside a directory?

Thanks.

---

### Post by toejamfootball on 2009-05-02
Well, I used my brain for once and figured it all out myself.

I had to remove the extra mount point I did this with

```
sudo rmdir /Slave
```

Now the only mount point left is the original one, and the Howto in my OP worked fine. The HDD is now mounting on startup and an Icon is displayed on the Desktop.

---

### Post by zeex on 2009-05-02
> **toejamfootball said:**
> Hi, I followed this HOWTO [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

I did this twice (because the first time, I wasn't expecting it to do what it did), so now the drive mounts in two different places.

I would like to just have it mounted in one place, how can I do this?

Also, is it possible to have it show up on the Desktop as a HDD, rather than just a Folder inside a directory?

Thanks.

Hi, 

Take a look at [this link]("http://stringofthoughts.wordpress.com/2009/04/16/auto-mount-window-drives-at-startup-ubuntu-810/"). I use it to mounts all my drives (FAT32 and NTFS) at startup. All the disks shows up on the desktop. I can still use gnome-mount gnome-unmount (the click mount utility of ubuntu). I've 16 drives. This comes really handy. 

Try it. (I use ubuntu 8.10)

---

### Post by toejamfootball on 2009-05-02
> **zeex said:**
> Hi, 

Take a look at [this link]("http://stringofthoughts.wordpress.com/2009/04/16/auto-mount-window-drives-at-startup-ubuntu-810/"). I use it to mounts all my drives (FAT32 and NTFS) at startup. All the disks shows up on the desktop. I can still use gnome-mount gnome-unmount (the click mount utility of ubuntu). I've 16 drives. This comes really handy. 

Try it. (I use ubuntu 8.10)
Thanks I'll check it out!

---

