---
title: "Mounting root filesystem ignoring permissions plzhelp!"
date: 2009-05-25
forum: General Help
---

### Post by nazdrug on 2009-05-25
I have a bunch of folders which look like this:

```
d--------- 28 root root   4096 2009-05-21 23:25 folder1
d---------  4 root root   4096 2009-05-21 10:56 folder2
d--------- 35 root root   4096 2009-05-18 07:35 folder3
drwxrwxr-x 11 root deploy 4096 2009-05-15 09:39 ..
drwxrwxrwx 15 user user   4096 2009-05-03 02:12 .
d---------  2 root root   4096 2009-05-03 02:12 folder3
d---------  2 root root   4096 2009-05-03 02:12 folder4
d---------  2 root root   4096 2009-05-03 02:12 folder5

```

But cannot sudo rm -rf .
I get operation not permitted on each of the folders!! I need a way to remove these folders!!! So I'm thinking mounting the root partition ignoring ALL permissions for a while and changing back after I've removed the folder.

What do I need to change in my fstab file to ignore all permissions?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=13aff735-f638-4a3c-b832-320bf48c02e4 /               ext3    relatime,errors=remount-ro 0       1

```

Thanks so much in advance :)

---

### Post by fballem on 2009-05-25
Permissions are a key part of Linux - you do not want to turn them off! This is part of what keeps Linux relatively safe from viruses.

I don't know what the files are that you are trying to delete, but I'm assuming that you _really_ want to delete them. I will run into this sometimes when I'm setting up extensions on OpenOffice and the extensions are downloaded as root ownership. In my case, I need to change the owner to myself in order to be able to work efficiently with these files.

If you open a terminal then type ```
gksudo nautilus
```, this will start nautilus with root permission. Go to the folders where these files are located. You can delete them this way.

Hope this helps,

---

### Post by nazdrug on 2009-05-25
Nah, this is via ssh.

Even in sudo bash I still can't delete anything....

---

### Post by satnelav on 2009-05-25
Are you trying to remove the directory '.'?

---

### Post by ecolitan on 2009-05-25
Isn't there something like a sticky bit which can be set or unset, which can stop you being able to delete files. Maybe investigate that.

---

### Post by fballem on 2009-05-25
> **nazdrug said:**
> Nah, this is via ssh.

Even in sudo bash I still can't delete anything....

At the risk of asking the obvious, if you're accessing a different machine through ssh, are you sure that you are accessing that machine using the root password for that machine? For example, if my machine is xyz-01 and I am accessing xyz-99 through ssh and want to delete these folders on xyz-99, I have to use the root password for xyz-99, not the root password for xyz-01.

---

### Post by nazdrug on 2009-05-25
No I used rm -rf . as an example.

I ssh'd in as a normal user.

sudo bash
enter password
I'm now root user (root@server:/path/to/folder#) -> At this point I should have FULL ROOT access correct, I should be able to do whatever the hell I want, right?
rm -rf folders

but NO ONE has permissions to the folders, hence the 'operation not permitted errors'. Even though root owns the folders and the contents within them.

Have a look at the ls -alt in the first post, how do I get access to these files again?!?!!

---

### Post by geirha on 2009-05-25
They might have some attributes set, like the immutable attribute.  What does "lsattr" say?

---

### Post by nazdrug on 2009-05-25
```
root@server:/path/to/folders# lsattr
----ia------------- ./folder1
----ia------------- ./folder2
----ia------------- ./folder3
----ia------------- ./folder4
----ia------------- ./folder5

```

What _should_ it say?

---

### Post by nazdrug on 2009-05-25
```
chattr -R -i .
```

MAGIC! Thanks for your help! The folders were immutable - weird!

---

