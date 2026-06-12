---
title: "Missing space in /var"
date: 2009-03-30
forum: General Help
---

### Post by kasper22 on 2009-03-30
Ok,  Well I don't know if it's a file or not, but something strange is happening.  My /var directory is on its own partition and 2.8GB.  This is the output from dh:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             2.8G  275M  2.6G  10% /
tmpfs                 3.7G     0  3.7G   0% /lib/init/rw
varrun                3.7G  532K  3.7G   1% /var/run
varlock               3.7G     0  3.7G   0% /var/lock
udev                  3.7G  3.0M  3.7G   1% /dev
tmpfs                 3.7G     0  3.7G   0% /dev/shm
lrm                   3.7G  2.4M  3.7G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda5              92M   33M   55M  38% /boot
/dev/sda3              66G   25G   42G  37% /home
/dev/sda7             5.6G  3.0G  2.6G  54% /usr
/dev/sda6             2.8G  2.6G  287M  90% /var

```
However when I run du -h /var I get this:
```

...
272M	/var

```
Anyone have any ideas how I can track down this missing space or what might cause this?

Bryan

---

### Post by ibuclaw on 2009-03-30
You may not have the permissions to read/list most the files:
try:
```
du -h /var --max-depth=0 2>/dev/null
```
Followed by
```
sudo du -h /var --max-depth=0
```
And note the difference.

Regards
Iain

---

### Post by kasper22 on 2009-03-30
Sorry, the du I ran before was with sudo.  Without sudo /var is 260MB.  So all files should be accounted for.

---

### Post by ibuclaw on 2009-03-30
From what you've given. It looks like the information from **df** is slightly outdated. As in, you **did** have 287MB of space available, but this changed after some cached files got cleared up. (ie: sudo apt-get clean).

I've had this happen once or twice when I had issues with flooding log files a while back. Even though I remove nearly 20GBs of data, df was still showing a full disk. To update the information, I rebooted my computer.
If the information from displayed **df** is still persistent after you perform a system reboot, then I'll have a look deeper into this.

Regards
Iain

---

### Post by kasper22 on 2009-03-31
I hate not knowing what was using that space and using a windows fix to get things back to normal, but restarting did the trick.  Now df is showing the correct value again.

---

