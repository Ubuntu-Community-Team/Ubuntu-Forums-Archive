---
title: "Hard Drive Space has disappeared?"
date: 2006-02-10
forum: Desktop Environments
---

### Post by tgbp492 on 2006-02-10
OK, first post ever please be gentle.

I am a total NOOB to Ubuntu.  I love it though!!!  I will never go back to windows... EVER.  However I have a problem.  Running Ubuntu 5.10 and not having any problems for a week or so.   Last night while I slept my free hard drive space went from 22 Gig to   0  FREE SPACE when I woke up.  I have looked high and low, even in hidden files and can find NO NEW files.  Where did all that space go?  I can't view media files and the such because there is no free space.   As well as other problems.  Anyone have any ideas?   Was I hacked and someone put some stuff on my drive?  I ran rkhunter and came up OK on everything.  So I don't think so.  Please someone ideas?  What other information do I need to post?  It's a 30 Gig Western Digital hard drive.

Thanks!!!!!!

Big Tim

---

### Post by jasmuz on 2006-02-10
Do this

$ df -h 

$ sudo apt-get clean

$ sudo df -h

---

### Post by Zeroangel on 2006-02-10
That's a toughy.

 If I were you i'd run the command 'gksudo nautilus' (so you can delete files that are owned by root, if that is necessary), right-click -> properties on all your major directories (ie: /home, /usr, /tmp, /var etc) and find out what's eating up several gigs of space. Once you find that, descend into it and do the same on the subdirectories, eventually you will find the culprit.

---

### Post by angkor on 2006-02-10
could you please post the output of the above mentioned command```
df -h
```

---

### Post by tgbp492 on 2006-02-10
results

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              28G   27G     0 100% /
tmpfs                 126M  4.0K  126M   1% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-9-386/volatile


( And Thanks already ! \\:D/  )

BigTim

---

### Post by tgbp492 on 2006-02-10
Results after running  

```
sudo apt-get clean
```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              28G   26G  355M  99% /
tmpfs                 126M  4.0K  126M   1% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-9-386/volatile

```

Big Tim

---

### Post by halfvolle melk on 2006-02-10
Hi,

you might want to try
```
du|sort -n
```
then wait a few seconds and check out the bottom of the list.

---

### Post by tgbp492 on 2006-02-10
Thank you everybody!  I did as asked and found the problem.  It is in my 

```

/var/log/gnump3d/error.log

```
the error.log was 22.3 Gigabytes!!  I just emptied it and voila good for now.  

Anyone have any idea how to disable debug in gnump3d or any other ideas for a permanent fix?

Thank you all for your time and any ideas for a permanent fix.

Big Tim

---

### Post by firdgerator on 2006-02-10
You might also have a hard drive leech! See if this works for you: [http://harddriveleech.tripod.com]("http://harddriveleech.tripod.com")

---

### Post by dcstar on 2006-02-10
[QUOTE=tgbp492]Thank you everybody!  I did as asked and found the problem.  It is in my 

```

/var/log/gnump3d/error.log

```
the error.log was 22.3 Gigabytes!!  I just emptied it and voila good for now.  

Anyone have any idea how to disable debug in gnump3d or any other ideas for a permanent fix?
.....[/QUOTE]
There is probably a .conf file for this somewhere, you will have to find it and then see if you can change the log options.

---

