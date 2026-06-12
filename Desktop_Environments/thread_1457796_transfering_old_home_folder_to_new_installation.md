---
title: "transfering old home folder to new installation"
date: 2010-04-19
forum: Desktop Environments
---

### Post by mr.g on 2010-04-19
Dear all,

I have a home directory in another system(7.10) with the user name "xyz".  I just installed a copy of 9.10 and would like the user xyz to use my new system, with the same files in its old folder.  Is there any way to achieve this?  On 9.10, I have tried to add a new user "xyz" and overwrite its home directory with the old xyz home directory.  This does not work. (It can't login when I restart the computer.)  Would any experts tell me what to do?

G

---

### Post by micio on 2010-04-19
strange... I have a home partition shared between 2 linux distros...

however it could be a permission problem, backup you home with

```
tar pzcvf tarball.tgz 
```

and decompress to other system with 

```
tar pxvf tarball.tgz
```

---

### Post by mick222 on 2010-04-19
Iran into problems sharing a home partition between suse and Ubuntu . The problem is you copy over older versions of programs in the hidden files things like links to firefox for flash that havn't been installed system wide . I think the easiest way is to create a user with the name you want then just copy and paste the data into it.

---

### Post by Boondoklife on 2010-04-19
or just create a new user and put their older home folder on the desktop. They can then get what ever info they need from it.

---

### Post by grege on 2010-04-20
My solution is simple enough. Boot to a maintenance prompt and rename the /home/name folder to /home/name.old This maintains permissions/ownership to your chosen login name. Install new version and set up a user with the name you want. Once running you can drag and drop from the name.old to name without any problems. Enable "view hidden files" in Nautilus. Do not copy across config files from four versions ago that is asking for trouble - just docs, music, video, favorites and email.

I always have midnight commander installed to make it simple to rename, move and copy files without having to remember command line syntax.

sudo apt-get install mc

---

