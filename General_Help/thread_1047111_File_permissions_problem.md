---
title: "File permissions problem?"
date: 2009-01-22
forum: General Help
---

### Post by porchrat on 2009-01-22
Hi all I have a particular user (lets call this user "foo") on this machine and I wanted to stop other users being able to access that users /home directory.

What I did was recursively let the users /home directory have permissions set to u=wrx and no permissions at all for "group" or "other".

Now when I set the users /home directory to allow "g+rx" MY user (lets call it "bar") doesnt have permission to view or navigate into the directory.

Basically "bar" belongs to group "foo", but "bar" is still incapable of navigating into "foo", even though "foo" has g=rx" permissions.

I really don't understand this.

---

### Post by yeats on 2009-01-22
Can you ls -l /home and post the output here?  That might help . . ..

---

### Post by drs305 on 2009-01-22
When you changed the permissions to allow access did you do it recursively as you did when you removed permissions for group and others? Or did you just want foo's $HOME accessible without the subfolders?

Run these to confirm bar belongs to group foo and check the permissions:
```

id bar
ls -lad /home/foo

```

---

### Post by porchrat on 2009-01-22
> **drs305 said:**
> When you changed the permissions to allow access did you do it recursively as you did when you removed permissions for group and others? Or did you just want foo's $HOME accessible without the subfolders?

Run these to confirm bar belongs to group foo and check the permissions:
```

id bar
ls -lad /home/foo

```

Yup checked it and they definitely belong...I will post the outputs with the names edited as I am a paranoid about people knowing my username (the toaster told me to do it) :)

Here we go:
```
id bar
uid=1000(bar) gid=1000(bar) groups=1000(bar),4(adm),107(fuse),109(lpadmin),115(admin),1002(foo)
```

```
id foo
uid=1002(foo) gid=1002(foo) groups=1002(foo),4(adm),30(dip),46(plugdev),107(fuse),115(admin)

```

I removed some of the other irrelavent groups they belong to for easier reading

```
 ls -l /home
total 24
drwxr-x--- 41 foo foo 4096 2009-01-21 08:30 foo
drwx------ 82 bar        bar        4096 2009-01-22 11:55 bar

```

Please note that I have removed the usernames that don't matter and that these usernames have been changed to protect the innocent.

Also I did it recursively, I need access to the subdirectories as well.  It's just that I don't want to have to "sudo su", or "sudo su foo" just to browse the other users /home.

---

### Post by porchrat on 2009-01-22
> **drs305 said:**
> When you changed the permissions to allow access did you do it recursively as you did when you removed permissions for group and others? Or did you just want foo's $HOME accessible without the subfolders?

Run these to confirm bar belongs to group foo and check the permissions:
```

id bar
ls -lad /home/foo

```

Also even if I hadn't done it recursively, I still should be able to "cd" into the /home/foo directory and I can't....weird.  I'm sure it is one of those forehead-slapping moments where I have missed something that is brutally obvious .

---

### Post by drs305 on 2009-01-22
Have you gone into System, Admin, Users & Groups and seen what it shows? Should be able to get the same info from the command line but it might show something that's not jumping out at you. (us)

---

### Post by porchrat on 2009-01-22
> **drs305 said:**
> Have you gone into System, Admin, Users & Groups and seen what it shows? Should be able to get the same info from the command line but it might show something that's not jumping out at you. (us)

Yes I've checked it...looks like the GUI has the same information that the command line has.  This is rather strange.  Perhaps a restart is in order, but I doubt that is the issue as I have never had to restart to have file permissions take effect before. :(

---

### Post by porchrat on 2009-01-22
No one have any ideas?...personally I'm stumped by this, although I'm not exactly a guru on Linux file permissions.

Perhaps I have misunderstood how file permissions work.

If user1 is a member of the "user2" group then shouldn't user1 be able to browse those directories with group="user2", whether or not user2 belongs to the "user1" group?

---

### Post by porchrat on 2009-01-28
Believe it or not this problem seems to have resolved itself with a restart.  Anyone else experienced this before?  A situation in which a restart was required to get the file permissions changes to take effect?

Strange.  Thanks for your help and advice all.

---

