---
title: "Can't log in &quot;Authentication Failed&quot; [Intrepid]"
date: 2008-11-24
forum: Desktop Environments
---

### Post by missmaryrules on 2008-11-24
After installing a new login theme and disabling Automatic Login, I can't log in. When I rebooted and got to the login screen, it displayed "..." as the username and gave me an "Authentication Failed" error; clicking the "OK" for the error message doesn't make it go away and I an unable to type my username/password.

Not only am I unable to log in, but am also unable to copy files (schoolwork!) from my documents using the live disc to navigate.

How can I again enable automatic login or at least copy those files to an external hard drive?

---

### Post by taurus on 2008-11-24
If you want to copy files from your $HOME to an external drive from the LiveCD, you first need to mount the partition where /home is or / if you have only one partition.  Assuming it's /dev/sda1, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
ls -la /media/ubuntu/home
```

---

### Post by missmaryrules on 2008-11-24
> **taurus said:**
> If you want to copy files from your $HOME to an external drive from the LiveCD, you first need to mount the partition where /home is or / if you have only one partition.  Assuming it's /dev/sda1, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
ls -la /media/ubuntu/home
```

I managed to get it to boot normally again by editing the file "gdm.conf-custom" (in the /home/etc/gdm folder on my ubuntu partition); the settings for "TimedLoginEnable" and "AutomaticLoginEnable" were set to "false", so I changed them to "true".

Thanks for the info on copying files, though!

---

