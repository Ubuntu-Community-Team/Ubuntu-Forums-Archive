---
title: "Two drive partitions in Conky"
date: 2009-05-06
forum: Desktop Environments
---

### Post by lixy on 2009-05-06
Hi all,

I played around with somebody's conkyrc to customize it, and it now looks exactly like I want it to. 

The only issue I have is that the original file just listed usage for the root of the filesystem. I've learned the hard way to always separated your /home from the rest by putting it on separated partition. But when I tried just modifying the original by changing / to /home to get the usage for my home partition, the free percent and the display bar don't match my real usage. The ration displayed by the first two variable is alright though.

Here's the relevant section. The first line was taken as is and works perfectly. The second one is how I modified it to display another partition, and that's the one I'm having trouble with. 

> 
Root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}% ${fs_bar /}
  
Home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}% ${fs_bar /home}

Thanks for any tips,

---

### Post by kpkeerthi on 2009-05-06
Can you post a screen of conky displaying the usage of /home and the output of the below command?
```
df -h
```

---

### Post by lixy on 2009-05-06
> **kpkeerthi said:**
> Can you post a screen of conky displaying the usage of /home and the output of the below command?
```
df -h
```

Screenshot is attached and df -h spits out the following:

> /dev/sda7             6.4G  3.5G  2.5G  59% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  168K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5              84G  242M   79G   1% /home

Thanks for taking the time to look at it.

---

### Post by mcduck on 2009-05-06
> **lixy said:**
> Screenshot is attached and df -h spits out the following:



Thanks for taking the time to look at it.

Your home is 84GB partition, out of which 79GB is available for users (5% of disk space on Ext filesystems is reserved for root only). The reason for the difference between df output and what Conky reports is that df tells the available space for the current user's point of view, while Conky reports the absolute diks use from the system's point of view.

You can easily see the difference if you run "df -h" and "sudo df -h". When ran with "sudo", df will report more available disk space than when ran with normal user privileges.

---

### Post by lixy on 2009-05-06
> **mcduck said:**
> Your home is 84GB partition, out of which 79GB is available for users (5% of disk space on Ext filesystems is reserved for root only). The reason for the difference between df output and what Conky reports is that df tells the available space for the current user's point of view, while Conky reports the absolute diks use from the system's point of view.

You can easily see the difference if you run "df -h" and "sudo df -h". When ran with "sudo", df will report more available disk space than when ran with normal user privileges.

Nah. Running the command with sudo gives the same output.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             6.4G  3.5G  2.5G  59% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  168K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5              84G  251M   79G   1% /home
```

But now I notice that even the root filesystem's percentage is off. It wasn't as apparent because 39% is not that far off 59% while 1% can't possibly be confused with 94%.

---

