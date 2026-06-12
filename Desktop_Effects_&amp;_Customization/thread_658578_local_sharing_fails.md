---
title: "local sharing fails"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by roschell on 2008-01-04
I need to set up a folder which will be shared for local users on one machine. It would be good to have such in /home folder as it is a separate partition. How do I create it in Ubuntu? 

I tried two options which failed:
1.
Created folder /sharedocs in Desktop and gave permissions to other users, these very actually by default with access allowed. In other users' account however nothing appeared on the Desktop as /sharedocs

2.
Put the users into the same group and repeated the step 1.

Thanks in advance

---

### Post by roschell on 2008-01-15
Any ideas? 

Thanks...

---

### Post by Forlong on 2008-01-15
The desktop is nothing else then a directory. You can't have one folder in *every* desktop directory.

You can however use symlinks.
Let's say you have a directory called /home/sharedocs

Now link that folder on the user's desktops:
```
ln -s  /home/sharedocs /home/user1/Desktop/sharedocs
```
```
ln -s  /home/sharedocs /home/user2/Desktop/sharedocs
```
etc.

---

