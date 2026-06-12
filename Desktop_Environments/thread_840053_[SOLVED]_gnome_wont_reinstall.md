---
title: "[SOLVED] gnome wont reinstall"
date: 2008-06-25
forum: Desktop Environments
---

### Post by Yondergod22 on 2008-06-25
hi. I changed my partition sizes with gparted, and somehow gnome got messed up, I posted a thread for help about that, and someone told me to purge gnome, then reinstall it, so I purged it, now it wont reinstall. these are the things I ran to to try to reinstall it
**sudo apt-get install gnome base**
```
the following packages has unmet dependencies:
  gnome: depends: gnome-desktop-environment (= 1:2.20.2.2)but its not going to be installed
E: broken packages
```
then I did **sudo apt-get install gnome-desktop-environment** and got
```
the following packages has unmet dependencies:
  gnome: depends: gnome-keyring-manager(= 1:2.20.2.2)but its not going to be installed
E: broken packages
```
so I did **sudo apt-get install gnome-keyring-manager** and got...
```
package gnome-keyring-manager is not available, but is referred to by another package
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: package gnome-keyring-manager has no installation candidate
```
and I tried **sudo apt-get -f install package**and it didn't help.
anyone know how to get gnome back?
Thank You

---

### Post by p_quarles on 2008-06-25
Try running:
```
sudo dpkg --configure -a
```
I don't expect any better results from that, but it's one of those standards that's worth a shot before moving on to the heavy-duty problem fixing.

After that, try posting the results here of this command:
```
cat /etc/apt/sources.list
```

---

### Post by Yondergod22 on 2008-06-25
> **p_quarles said:**
> Try running:
```
sudo dpkg --configure -a
```
I don't expect any better results from that, but it's one of those standards that's worth a shot before moving on to the heavy-duty problem fixing.

After that, try posting the results here of this command:
```
cat /etc/apt/sources.list
```
nope, the first one didn't work. and heres cat /etc/apt/sources.list:
[IMG]http://i235.photobucket.com/albums/ee210/yondergod2/100_1451.jpg[/IMG]

---

### Post by Yondergod22 on 2008-06-25
If I copy my home folder to another partition, then reinstall ubuntu, then copy it back would I have all my installed applications and stuff?

---

### Post by p_quarles on 2008-06-25
> **Yondergod22 said:**
> If I copy my home folder to another partition, then reinstall ubuntu, then copy it back would I have all my installed applications and stuff?
No, that wouldn't keep your installed applications, but it would keep all of your personalized settings. And the applications are easy to reinstall.

BUT, I would hold off to see if someone here can provide some further ideas for fixing the problem. Of course, if this is urgent, you may have no choice but to reinstall, but I imagine this can be fixed fairly easily by someone with the right knowledge.

---

### Post by Yondergod22 on 2008-06-25
im just gonna reinstall b/c I want to make a separate /home partition anyways

---

