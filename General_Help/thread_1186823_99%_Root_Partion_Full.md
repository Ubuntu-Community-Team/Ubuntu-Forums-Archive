---
title: "99% Root Partion Full??"
date: 2009-06-13
forum: General Help
---

### Post by gsgentry on 2009-06-13
I am getting an error when starting Ubuntu 8.04 stating that my root partition is 99% full. I am running a Dell Mini 9 with a 4GB hard drive. I have not loaded or placed any files on this machine as it is only for the internet. I have downloaded all of the updates though so I am guessing this is what has loaded up my computer.

Any suggestions on what to do to free up some space?

Here are my results from df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  2.8G  447M  87% /
varrun               1009M   72K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   36K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M  1.9M 1007M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon      3.4G  2.8G  447M  87% /home/sky/.gvfs
```



.

---

### Post by drs305 on 2009-06-13
You can look at this wiki guide. It will give you the commands to analyze what is going on in your system partition. It is fairly comprehensive. If you don't understand or have questions you can post them here.

One of the common things is undelete trash, either your trash or system trash. You can check your system trash with the following command. Use SHIFT-DELETE to remove the 'Trash' folder. If you don't have a Trash folder there it means you don't have any system trash.
```
gksudo nautilus /root/.local/share/
```

[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Added:
Another very simple thing you can try to make some space - remove downloaded packages. You don't need to save the packages on your computer:
```

sudo apt-get clean
sudo apt-get autoclean

```

---

### Post by xebian on 2009-06-13
> **gsgentry said:**
> I am getting an error when starting Ubuntu 8.04 stating that my root partition is 99% full. I am running a Dell Mini 9 with a 4GB hard drive. I have not loaded or placed any files on this machine as it is only for the internet. I have downloaded all of the updates though so I am guessing this is what has loaded up my computer.

Any suggestions on what to do to free up some space?

Here are my results from df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  2.8G  447M  87% /
varrun               1009M   72K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   36K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M  1.9M 1007M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon      3.4G  2.8G  447M  87% /home/sky/.gvfs
```



.
Run this on a terminal
sudo aptitude clean will get rid of the packages downloaded.

---

### Post by gsgentry on 2009-06-13
Awesome... that worked. That also resolved some other issues that I was having!!!:)

 Now if I could get my wireless working again from my stupidity of removing packages on my own. :( I guess I removed the wrong thing and now my wireless is not working. LOL

In case anyone is up for the challenge, the post is here...

[http://ubuntuforums.org/showthread.php?t=1186797]("http://ubuntuforums.org/showthread.php?t=1186797")


Thanks a million!!!

---

