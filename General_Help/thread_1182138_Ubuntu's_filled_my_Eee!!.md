---
title: "Ubuntu's filled my Eee!!"
date: 2009-06-08
forum: General Help
---

### Post by t0p on 2009-06-08
I've got an Asus Eee PC 701 - one of the old "original" netbooks with a 4 gig SSD.  Last week I installed Jaunty NBR on it.  I have a 4 gig SD card in the card reader slot full-time, so I put / on the SSD and /home on the card - 4 gigs each, I figured that would give the system room to grow into.  Right?

Wrong!  Today was the first software update since the installation, and now there's less than 1 gig in /!  Check it out:

```
ghost@machine:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.6G 1001M  72% /
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  104K  245M   1% /var/run
varlock               245M  4.0K  245M   1% /var/lock
udev                  245M  152K  245M   1% /dev
tmpfs                 245M   96K  245M   1% /dev/shm
lrm                   245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             3.8G  1.5G  2.1G  42% /home
ghost@machine:~$ 

```

This is crazy.  I'm gonna fill the machine in no time.

I've now set the updates so I only get the security updates.  And I'm going to get an 8 gig SD card, then I'll reinstall so / is on the card and /home is on the SSD.  Hopefully that'll be enough space.  But I won't be able to get the card for a while.  So what I want to know is this:

Is it possible to give, say, 1 gig of the SD card to /?  So 3 gigs of the SD card belongs to /home and the other gig goes to / on the SSD, increasing / to 5 gigs?  How do I do this?  Preferably without reinstalling - I've still got the live USB - but I will reinstall if necessary.

What annoys me is that this is supposed to be the "netbook remix".  Okay, I know some netbook hard drives nowadays have > 100 gigs.  But I still reckon a netbook remix should be tiny, so as to accommodate the venerable Eee.  Don'tcha think?

---

### Post by ajgreeny on 2009-06-08
I've no specific idea about the netbook remix of ubuntu, but make sure that /var/cache/apt/archives is emptied as it can use a lot of room with all the update packages that are cached there, if you do not remove them.  A standard ubuntu install takes about 2.3 - 2.4 GB if I remember correctly, with nothing added, so a few hundred MB of update packages could easily use up the space quickly.  As an example, mine is over 400MB, but I'm not short of space so don't usually empty it.

---

### Post by Therion on 2009-06-08
Try using the House Cleaning option (#12) of **QuickStart**:

[http://quickstart.freeforums.org/quickstart-download-pics-t2.html](http://quickstart.freeforums.org/quickstart-download-pics-t2.html)

That should free some space.

---

### Post by Hairy_Palms on 2009-06-08
sudo apt-get clean 
removes all apt cache files from the system, can collect a lot of stuff from updates, i once had over 2GB of old packages in there.

---

