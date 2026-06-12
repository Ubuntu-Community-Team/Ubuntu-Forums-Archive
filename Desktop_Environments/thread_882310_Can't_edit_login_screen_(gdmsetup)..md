---
title: "Can't edit login screen (gdmsetup)."
date: 2008-08-06
forum: Desktop Environments
---

### Post by kaoskorruption on 2008-08-06
When I go to System -> Administration -> Login Window, the program opens for half a second and the closes. I've searched and searched for a fix, but I can't find anything. I tried entering the same command that clicking on Login Window in the Administration menu uses (gksu /usr/sbin/gdmsetup) and unlike the other topics I've seen on this, there is nothing about a Segmentation fault in the console. Nothing. It just looks like this:

```
chris@Phantom:~$ gksu /usr/sbin/gdmsetup
chris@Phantom:~$ 

```

I do use Compiz-Fusion, but the problem occurs even when I have it disabled. Any help would be appreciated.

---

### Post by aysiu on 2008-08-06
[This](http://www.psychocats.net/ubuntu/fixsudo) may help.

---

### Post by kaoskorruption on 2008-08-06
No, sudo works perfect. It's something else :(

---

### Post by lori on 2008-08-09
> **kaoskorruption said:**
> When I go to System -> Administration -> Login Window, the program opens for half a second and the closes. I've searched and searched for a fix, but I can't find anything. I tried entering the same command that clicking on Login Window in the Administration menu uses (gksu /usr/sbin/gdmsetup) and unlike the other topics I've seen on this, there is nothing about a Segmentation fault in the console. Nothing. It just looks like this:

```
chris@Phantom:~$ gksu /usr/sbin/gdmsetup
chris@Phantom:~$ 

```

I do use Compiz-Fusion, but the problem occurs even when I have it disabled. Any help would be appreciated.


Same thing is happening to me except I **do** get "segmentation fault".

I've searched high and low and can't find any resolutions for this problem. Don't know what caused it, login Window worked fine several days ago. :(

---

### Post by lori on 2008-08-09
My problem has been resolved with RomeReactor's solution which can be found [here]("http://ubuntuforums.org/showpost.php?p=5433920&postcount=8").

---

### Post by oVIXx on 2008-08-13
I have the same problem which started about a week ago with a gdm security update. More info on this re-occurring bug can be found at 

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/208979]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/208979")

---

### Post by oVIXx on 2008-08-13
Or just use "sudo dbus-launch gdmsetup" as a work around.

---

### Post by kaoskorruption on 2008-08-17
Now it's working... all I've done is waited one week, rebooted, and applied some updates. I don't know if any of that has anything to do with it but problem no longer applicable. Thanks for all of your help.

---

