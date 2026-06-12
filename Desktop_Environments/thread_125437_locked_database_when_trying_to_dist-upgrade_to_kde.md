---
title: "locked database when trying to dist-upgrade to kde 3.5.1"
date: 2006-02-03
forum: Desktop Environments
---

### Post by Rory on 2006-02-03
Just tried to upgrade from 3.5 to 3.5.1.  Everything went smoothly until a message in terminal said that a script had changed and gave me the option of upgrading to the new one, keeping the old one or comparing them by selecting 'D'.  

So, I selected 'D'.  I saw the comparison and decided I wanted to upgrade to the new one.  But I was locked in the comparison of the script with (END) at the bottom.  

Eventually, I stupidly closed terminal and re-opened.  The next time I did apt-get update, apt-get upgrade, I got the following:

```

rory@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
rory@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
rory@ubuntu:~$      

```


Can anyone help?  Getting caught between upgrades certainly not ideal.

Thanks,
Rory

---

### Post by sfabel on 2006-02-04
Easy. :)

Find the still running/sleeping/dead processes of apt-get and kill them:

```
ps auxwww | grep apt-get
```

Will give you all running apt-gets plus the user they're running as. In the first column you'll probably see "root".

To kill the process(es), use:

```
sudo kill [Process ID]
```

Cheers,
Stephan

---

### Post by Rory on 2006-02-04
Thank you for your help!! :)

---

