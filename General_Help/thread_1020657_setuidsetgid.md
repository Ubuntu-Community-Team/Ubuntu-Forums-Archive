---
title: "setuid/setgid"
date: 2008-12-24
forum: General Help
---

### Post by petersohn on 2008-12-24
I found the following problem on my Ubuntu 8.10 system: when I boot up with my wifi disabled by hardware, and then I turn it on, the network interface is still down. So I did the following workaround: when I want to use the wifi, and turn it on, I type in the terminal
```
sudo ifconfig wlan0 up
```

This works well, but it's a bit uncomfortable that I have to type in the password every time I want to turn on the wifi.

So I tried the following: I made a file named wifiup.sh. It looks like the following:
```
#!/bin/bash
ifconfig wlan0 up
```
I chowned it root:root, chmod-ed it setuid/setgid (6755), and moved it to /usr/local/bin. If I ls it now, it looks like this:
```
-rwsr-sr-x 1 root root 30 2008-12-23 10:48 /usr/local/bin/wifiup.sh
```

However, if I run it simply as "wifiup.sh", then I get permission denied. If I run it with sudo, it works however.

My question is the following:
Shouldn't it, when I set the setuid/setgid bits, run as root even if I run it as user?

---

### Post by snova on 2008-12-24
> **petersohn said:**
> ```
**-rwsr-sr-x** 1 root root 30 2008-12-23 10:48 /usr/local/bin/wifiup.sh
```

However, if I run it simply as "wifiup.sh", then I get permission denied. If I run it with sudo, it works however.

My question is the following:
Shouldn't it, when I set the setuid/setgid bits, run as root even if I run it as user?

If you set a file as setuid, than it will run with the permissions of its owner no matter who runs it; setgid is the same, but for the group rather than the user.

It looks not to have executable bits set for all users. Try this:

```
sudo chmod a+x /usr/local/bin/wifiup.sh
```

---

### Post by petersohn on 2008-12-24
I know what setuid and setgid mean, but it doesn't seem to work for me. Your solution also didn't help. It seems that the file runs, but it doesn't have root privileges, as I expected.

---

### Post by albinootje on 2008-12-24
> **petersohn said:**
> 
My question is the following:
Shouldn't it, when I set the setuid/setgid bits, run as root even if I run it as user?

First of all, you made the script +s and not the ifconfig binary.

And it's maybe more complicated than that, here's an example with the mount command :

$ ls -la /bin/mount
-rwsr-xr-x 1 root root 92584 2008-09-25 15:08 /bin/mount
$ mount -a
mount: only root can do that

$ cp /bin/mount /tmp/
$ cd /tmp/
$ sudo chown adrian:adrian mount
$ sudo chmod u+s mount
ls -la mount
-rwsr-xr-x 1 adrian adrian 92584 2008-12-24 20:53 mount
$ ./mount -a
mount: must be superuser to use mount

It could be possible that some programs cannot run as normal user even with the setuid flag on.

You could try to make your user owner of the ifconfig command, and make the ifconfig binary setuid and try that.
But, remember, setuid files are in theory potential security risks already.

---

### Post by petersohn on 2008-12-25
So if I make a script setuid root, it is not the same if I ran the script as root? Then I will just stick to using sudo.

---

### Post by albinootje on 2008-12-25
> **petersohn said:**
> So if I make a script setuid root, it is not the same if I ran the script as root? Then I will just stick to using sudo.

I think setuid bash-scripts are not possible. It's all about the commands in the script itself.

If you really want you could create a new and restrictive user which is allowed to use sudo without password, and make that user use iwconfig with root permissions.
Look at the sudo manual page for options : man sudo

---

