---
title: "Clearing /var/tmp/kdecache"
date: 2012-07-08
forum: Desktop Environments
---

### Post by Erik1984 on 2012-07-08
When analyzing my disk space usage I noticed that a folder called kdecache-myname in /var/tmp is about 1.3 GB. All important kde settings shoud be stored in ~/.kde. Would it be safe to remove this cache folder or remove all content from it?

---

### Post by Erik1984 on 2012-07-10
*bump*

---

### Post by oldos2er on 2012-07-10
A bit of googling tells me this should be safe as long as it's done when KDE is not running. 

I deleted /var/tmp/kdecache-ann and haven't suffered any ill effects.

---

### Post by Erik1984 on 2012-07-10
Thanks for answering and trying this out of course. I googled for it first but couldn't find a conclusive answer. I will try it then (after making a backup to be sure). By 'KDE not running' you mean  that before logging in to the graphical desktop I should switch to a TTY an delete from there?

---

### Post by Erik1984 on 2012-08-20
Follow up:

I finally attempted to delete the kdecache folder from /var/tmp and it worked. It's like oldos2er described but here is exactly what I did:

- Log out from the current graphical session
- Switch to another TTY, I took tty1 (ctrl+alt+F1)
- Enter
```
sudo service kdm stop
```to kill the graphical desktop entirely.
- Navigate to:
```
cd /var/tmp
```- check what the name is of your cachefolder and:
```
rm -r kdecache-yourname
```no root privileges required to delete that folder as you own it.
- Now you can enter:
```
sudo service kdm start
```
To restart the graphical desktop and switch back to it. 

That should be it. I brought disk usage back to 73% from 82% Note that normally you don't have to do this, I just made my root partition too small.

---

