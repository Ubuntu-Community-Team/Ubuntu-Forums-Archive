---
title: "Creating a hard drive image -help"
date: 2009-01-24
forum: General Help
---

### Post by TheMemphisExperience on 2009-01-24
I need an application to create an exact copy of my hard drive as I want to swap out the stock drive on my laptop for a faster, larger, less power hungry model. 

I have had little success in finding an application.

---

### Post by cosine352 on 2009-01-24
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Zewbie on 2009-01-24
you can use a program called partimage.  Not sure if it's installed by default so you may need run this command in the terminal.

```

sudo apt-get update && sudo apt-get install partimage

```

---

### Post by TheMemphisExperience on 2009-01-24
Partimage is a little closer to what I want. 

This drive dual boots Vista and Ubuntu and I worry that the MBR may become lost if I don't do it just right. That's why I want an application that makes an exact copy of the entire drive. 

If partimage is as good as it gets though, I'll just have to make it work or boot Vista from an external and realize my dream of making this machine a single booting Ubuntu machine.

---

### Post by Zewbie on 2009-01-24
I've done a full backup and restore with XP pro without any boot issues and as of right now I doing a full backup and restore with Vista.

NTFS is experimental in partimage so before you make a image of the Vista partion make sure you run defrag.

---

### Post by hyper_ch on 2009-01-24
start a live cd, copy the drive with:

```

sudo dd if=/dev/sdX of=/dev/sdY

```

where /dev/sdX is your current drive and /dev/sdY is the new one.

That will do a 1:1 copy and then you can use gparted to enlarge the partitions.

Be carefull about entering the correct drive designations, otherwise you could overwrite your existing one.

---

