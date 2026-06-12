---
title: "disk seems full for no obvious reason (new install)"
date: 2009-01-21
forum: General Help
---

### Post by sa125 on 2009-01-21
Hi - I've just recently set-up a new 8.10 server and started installing some stuff, including gnome-desktop. All went well until yesterday when I wanted to install netbeans 6.5 and got an error saying ```
'there is not enough disk space to extract installation data'
```. using nautilus I can see there are 125Gb free (out of 160Gb), but I'm not sure where the error might be coming from. 

Also running **df** I get:
```

$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/md0             9158656  181472 8977184    2% /
tmpfs                 496587       3  496584    1% /lib/init/rw
varrun                496587      72  496515    1% /var/run
varlock               496587       3  496584    1% /var/lock
udev                  496587    5196  491391    2% /dev
tmpfs                 496587       3  496584    1% /dev/shm
lrm                   496587      17  496570    1% /lib/modules/2.6.27-9-generic/volatile
overflow              496587     103  496484    1% /tmp

```

Any ideas on how to diagnose or solve this issue?

---

### Post by hyper_ch on 2009-01-21
what's the output of
```

df -h

```

---

### Post by sa125 on 2009-01-21
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              139G  6.2G  126G   5% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  344K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  2.8M  1.9G   1% /dev
tmpfs                 1.9G  208K  1.9G   1% /dev/shm
lrm                   1.9G  2.4M  1.9G   1% /lib/modules/2.6.27-9-generic/volatile
overflow              1.0M  124K  900K  13% /tmp

```

---

### Post by hyper_ch on 2009-01-21
problem lies here:
```

overflow              1.0M  124K  900K  13% /tmp

```
to extract data it will required temporary storage space ;)

---

### Post by theozzlives on 2009-01-21
try running fsck from the live CD

---

### Post by sa125 on 2009-01-21
> **hyper_ch said:**
> problem lies here:
```

overflow              1.0M  124K  900K  13% /tmp

```
to extract data it will required temporary storage space ;)

So, how should I go about mending this? :)

---

### Post by hyper_ch on 2009-01-21
no clue really... why does it show as "overflow"?

try
```

sudo umount /tmp

```

---

### Post by vanadium on 2009-01-21
This could be an explanation: 

[https://answers.launchpad.net/ubuntu/+question/34535](https://answers.launchpad.net/ubuntu/+question/34535)
> The script responsible for mounting your /tmp as overflow is run at boot time (it is located in /etc/init.d/mountoverflowtmp). It runs a check to see if there is a minimum acceptable space on /tmp and if there is not, it mounts it overflow. It also checks for unneeded overflow tmpfs for /tmp and removes them if that is appropriate. That is why after you freed some disk space and rebooted everything went back to normal.

---

