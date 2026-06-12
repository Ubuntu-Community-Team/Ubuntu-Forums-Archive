---
title: "Superuser privleges?"
date: 2009-03-01
forum: General Help
---

### Post by jakenbake42 on 2009-03-01
So I'm a new user of dual-booted XP and Ubuntu 8.10, and I resized my partitions wrong :[
My XP has too little space, while Ubuntu has too much
So I went to disk manager in XP, and deleted an unknown partition that was about 2 GB, I thought it would give me space because I don't know what I'm doing here haha
and now in Ubuntu, I can not install updates, it says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Also, when I started my computer in Ubuntu, the loading bar comes up, and then it does a system check of some sort and everythings fine except for the failure of

[ 23712571 ] iTco_wdt: failed to reset NO_Reboot flag, reboot disabled by hardware

Are these related?
Anything I can do to fix these besides wipe my whole hard drive and start over?

Thanks in advance

---

### Post by taurus on 2009-03-01
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Rallg on 2009-03-01
Try the above advice first, if you can get into Ubuntu at all. Also try booting to Ubuntu "recovery" if necessary.

But it may be that you have munged your Ubuntu system. Windows does not necessarily recognize a non-Windows partition, calling it "unknown."

If you have to reinstall, then you probably do not need to reinstall Windows, just Ubuntu. If your system was in use, then it's probably a good idea to use a live Linux distro from USB, grab your valuable stuff from within the previous Ubuntu (if you can get in), and save it to another USB.

If you have valuable stuff on a partition that you inadvertently deleted, it is sometimes possible to grab the files and copy them out. Not sure if that can be done by Linux, or by a special utility program on Windows. It isn't easy, but it is do-able.

---

### Post by jakenbake42 on 2009-03-01
Thanks so much!!!
I'm amazed at how kind and helpful people are in the Buntu community :]

---

