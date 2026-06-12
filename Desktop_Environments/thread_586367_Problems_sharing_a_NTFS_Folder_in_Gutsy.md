---
title: "Problems sharing a NTFS Folder in Gutsy"
date: 2007-10-22
forum: Desktop Environments
---

### Post by leillo1975 on 2007-10-22
Hello Everybody! This is my first time in this forums. First of all, sorry, my english is very bad.

I have the following problem with my new installation of Gutsy (I'm a Ubuntu User since 6.06). The problem is that I can't mount ntfs folders. When I go to System->Administration->Shared Folders, and I add a new shared folder, I go to my ntfs partitión and I can't view the folders in the select folder dialog. If I go to the partitión with nautilus I have no problem. 

In the 7.04, I'm use ntfs-3g, and I have no problems, but in gutsy this driver is implemented.....

Can somebody helps me. I need to share this folders to make my work.

---

### Post by benerivo on 2007-10-22
I beleive this is a permissions problem. I think your ntfs partition is being mounted with only you and root being able to see the contents of it. First I had to change the entry for the mount in /etc/fstab for my ntfs partition as below...```
UUID=DRDC839FEWW97118TN /mnt/Storage    ntfs    gid=1000 0       0

```Then to make it become visible for everyone as as a samba share, I went to the folder in nautilus, right clicked it to get the properties and made sure 'Other Users' had read/write permissions. There's probably a better way to do it, but this worked for me.

---

### Post by Sirmatto on 2007-10-22
I too had this problem after installing Ubuntu 7.10.  There's a very easy way to fix it I discovered:

Do: sudo gedit /etc/fstab

All of my NTFS hard drives had the option "default,umask=007,gid=46"  I changed this to just "default" saved, closed fstab and restarted.  When I logged back on, SAMBA was able to access all of my NTFS partitions.  Not sure if this is a safe way to do it, but it works.

---

### Post by Robvdl on 2007-10-23
Yes, that works for me too.

Removed umask=007,gid=46 (which is plugdev group), and just replace with defaults.

Works a charm.

---

### Post by leillo1975 on 2007-10-23
Works fine. Thank you to all.:KS:KS:guitar::lolflag:

---

### Post by denar on 2007-10-29
thank u

---

### Post by paszczak on 2007-10-30
I think that better way is to change **umask=002** that means rwx rwx r-x ntfs folder will be still accesible via samba, but not everybody can write to ntfs drive. I think that is more secure than rwxrwxrwx (when you delete umask and gid)

---

### Post by padre44 on 2007-10-30
> **Sirmatto said:**
> I too had this problem after installing Ubuntu 7.10.  There's a very easy way to fix it I discovered:

Do: sudo gedit /etc/fstab

All of my NTFS hard drives had the option "default,umask=007,gid=46"  I changed this to just "default" saved, closed fstab and restarted.  When I logged back on, SAMBA was able to access all of my NTFS partitions.  Not sure if this is a safe way to do it, but it works.

You're a genius!  After messing around with this for several days, this finally worked.  Maybe I'm too new to Ubuntu to understand some of the complex instructions, but this was easy and it worked - thanks again.:)

---

### Post by dukejib on 2007-10-31
I agree

---

### Post by theShaggy on 2007-11-02
Hi guys!

I was having the same problem, and tried other solutions with no success.

However, when I changed the fstab.conf to just "defaults," it now lists all my Ubuntu shares on my XP machine,, but won't give me a login prompt as it used to.  It just tells me I don't have network access and refuses to let me in.  Other than that single line of code being removed, I'm not sure what I did differently, if anything at all.

I'll keep looking around, I'm sure I reset something somewhere along the way, however if removing the code is what caused it to go wonky, though I'd let you know.

*Edit*  Never mind, I think I had to reinitialize Samba when I rebooted - it might not have turned on for some reason.  Everything appears to be working perfectly (in fact, better than before!).  Thanks!

---

### Post by turbod33 on 2008-01-09
Any Idea how I would do this for a USB NTFS drive. I use it to share my media when I take it places, but for the most part it sits at home here.

---

