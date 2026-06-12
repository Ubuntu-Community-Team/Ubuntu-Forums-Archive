---
title: "System wont update packages"
date: 2005-08-25
forum: Desktop Environments
---

### Post by otey on 2005-08-25
Hi.

I have some trouble with ubdating some programs. I've been following the guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) and when calling the sudo apt-get upgrade command, i get the following message.

```
otey@osys:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gaim gaim-data gimp mozilla-firefox mozilla-firefox-gnome-support smbclient
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

What can i do to ubdate the packages?

---

### Post by GoA on 2005-08-26
Nothing, currently the problem is somewhere in the backports. I made a topic of the sama subject on other applications support forum and there is also one on the repositories forum.

---

### Post by otey on 2005-08-26
I followed an advice in some thread with a similar problem. I removed the backports from my sourcelist. 
Now my firefox is 1.0.6 and the other packages are updated as well.  :grin:

---

### Post by magnusbb on 2005-08-26
Here: [http://www.ubuntuforums.org/showthread.php?t=59874](http://www.ubuntuforums.org/showthread.php?t=59874)

---

