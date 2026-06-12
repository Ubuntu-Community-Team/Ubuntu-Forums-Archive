---
title: "Attempt at the Great Leap"
date: 2008-12-15
forum: General Help
---

### Post by EMABrad on 2008-12-15
I've been sick of Windows for years, it finally just won't start, and I'm making the shift to Feisty.  I have files in Windows that are of value to me.  I am currently booting with an ubuntu CD.  I need to know how to write the data from my computer onto external hard drive so that when I reformat my hard drive, I can put the files into ubuntu, but whenever I try, it says I do not have the permissions to write to it.

wat?

---

### Post by 3rdalbum on 2008-12-15
Your external hard drive should be formatted as fat32 or vfat. Ubuntu doesn't generally allow writing onto NTFS-formatted hard disks by default because it's a closed format of filesystem. At least, that's what I gather is the problem. I haven't had to mount an NTFS drive for years so I don't know how Ubuntu handles it these days.

If you do a search on Google for "ntfs-3g Ubuntu HOWTO", and follow a reasonably recent one, then you should be alright.

---

### Post by eldragon on 2008-12-15
you are using an old release too..

i recommend you to get the latest iso and use that instead, you wont find any trouble mounting ntfs partitions there.

check [www.ubuntu.com](www.ubuntu.com) to find out how to download the iso. you will need a working computer in order to burn it

---

### Post by howefield on 2008-12-15
If the file format is giving you problems, you can download ntfsprogs from Synaptic package manager, and set the drive to read/write. I have never tried that with the live cd, but I guess it should work.

If you still don't have access rights to the drive, you could open a terminal from your live cd and type

```
gksu nautilus
```

You should now be able to do your stuff.

---

### Post by linux_tech on 2008-12-15
What are your system specs? I'd recommend downloading 8.10.  Then create iso file and burn to cd and install.

---

### Post by scouser73 on 2008-12-15
I'm pleased that you are willing to try Ubuntu and I'm more than sure you'll be happy that you'll have made the right choice. 

I'd like to recommend that you use a newer version than Feisty Fawn, Ubuntu is currently at 8.10, aka Intrepid Ibex and as you are probably aware Ubuntu releases O/S updates every six months.  

I would suggest that you choose Ubuntu 8.04 LTS Desktop: Released April 2008 and maintained until April 2011 as this is release has **LTS** - Long Term Support.

Some further help are these free ebooks: [http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html")

Also a good site for looking things up is: [http://www.ubuntugeek.com/]("http://www.ubuntugeek.com/")

Any questions that you need answering have more than likely already been answered, and you are practically guaranteed a speedy answer, good luck with your installation and visit the forums as much as possible for any help that you may need.

---

