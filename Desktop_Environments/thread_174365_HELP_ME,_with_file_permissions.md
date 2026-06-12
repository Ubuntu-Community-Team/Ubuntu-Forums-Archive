---
title: "HELP ME, with file permissions"
date: 2006-05-11
forum: Desktop Environments
---

### Post by gazj on 2006-05-11
ok, i know how to change file permissions etc, but i have hit a slight problem with something more advanced i want to do, but someone must know how this can be done

This is what im trying to do

basically in my /home folder i have 2 users named gary and becky

and then i also have a folder called shared

ie
/home/gary                 owned by gary:gary
/home/becky               owned by becky:becky
/home/shared             owned by gary:shared

becky and gary both belong to a group called shared

now in the gary and becky folder i have symbolic links to the folders contained in shared witch is fine, ie we can both read write to theese directories

so everything is fine, until one of us created a file in one of the shared directories
because the new file is created by either gary:gary or becky:becky

so we can not read each others newly created files

i need someway that the files we create in theese directories are always owned by gary:shared, or even becky:shared with 755 permissions so we can both read, write them

hope this makes sense, any help would be great, thanks :)

---

### Post by aysiu on 2006-05-11
As far as I know, there's no solution. I've seen this problem brought up on the forums before, and no one offered an acceptable solution.

---

### Post by gazj on 2006-05-11
Damm, Thanks anyway

---

### Post by tonyr on 2006-05-11
Wait a minute.  I thought that's what having a common group membership
is all about.  If both **gary** and **becky** have primary group **shared**,
with default masks 660 (umask=6), then any file either creates should be owned by
<userid>:shared, and either should be able to access it.  

So let's lay it out:
  user **gary**, primary group **shared**, secondary group **gary**
  /home/gary owned by **gary:gary**
  user **becky**, primary group **shared**, secondary group **becky**
   /home/becky owned by **becky:becky**
  /home/shared owned by **gary:shared**

The permission mask on /home/shared would be 770 (drwxrwx---), meaning
that **gary** and anyone in group **shared** would have complete
access (read,write,delete) to anything in that directory.

And I sort of detect that there is some inclination to keep the two user directories
isolated from each other, in which case the permissions on /home/gary and 
/home/becky should be 700 (drwx------), so that even though files in those
directories have group access permission (-rw-rw----), neither user can get into
the other's directory to see them (hence the use of /home/shared directory).

OK, maybe this is a little dense.  Let's try a step by step.
1. Using Users&Groups management, make gary's primary group **shared**
and his secondary group **gary**.  Then make becky's primary group
**shared** and her secondary group **becky**.
2. Fix the home directories ownership and permissions (shown for completeness)
sudo chown gary.gary /home/gary
sudo chmod 700 /home/gary
sudo chown becky.becky /home/becky
sudo chmod 700 /home/becky
sudo chown gary.shared /home/shared
sudo chmod 770 /home/shared

In both gary's and becky's home directories, there needs to be an addition
to .login (or .profile or .cshrc or whatever shell login/startup script there
is) that says **umask 6**. I think there is also a way to do this umask
thing on a per-directory basis, but I don't recall what it is right now.

Now let's say gary logs in and creates a file (wait for it) **foo.txt**.  It should show up
like this:
-rw-rw---- 1 gary  shared 0 2006-05-11 16:19 **foo.txt**
and if he copies it to /home/shared, it should show up the same way there.
At that point, becky can read and write **/home/shared/foo.txt** because 
she belongs to group **shared**.  Likewise for becky creating a file
(**foobar.txt**?) and copying it to /home/shared.

Or have I completely missed the point here (i.e. you don't want gary and becky
to belong to a common group?).

---

### Post by tonyr on 2006-05-11
[QUOTE=tonyr]I think there is also a way to do this umask
thing on a per-directory basis, but I don't recall what it is right now.
[/QUOTE]

Uh, that is only in Solaris, I now do recall.  That's what I get for having been in
this business for too long.

---

### Post by gazj on 2006-05-14
Ok, i have managed to write a script that will change the owner and group of all the files in the /home/shared directory, all i need to do now is make it so this script is ran by root on logout, its a bad workround but the only one i can think of, anyone have any ideas how to run this script on logout

---

### Post by ametade on 2006-05-14
Hi there,

why don't you try setting the SGID attributte to the directory you wan't to share:
```

sudo mkdir /home/shared
sudo chown gary:shared /home/shared
sudo chmod g+s /home/shared

```

This way, all the files created inside /home/shared will have "shared" as group. At least, I think so...

---

### Post by tonyr on 2006-05-14
> 
This way, all the files created inside /home/shared will have "shared" as group. At least, I think so...


Seems to work that way, but it's only good if both users belong to group **shared**.

---

### Post by gazj on 2006-05-15
[QUOTE=ametade]Hi there,

why don't you try setting the SGID attributte to the directory you wan't to share:
```

sudo mkdir /home/shared
sudo chown gary:shared /home/shared
sudo chmod g+s /home/shared

```

This way, all the files created inside /home/shared will have "shared" as group. At least, I think so...[/QUOTE]

I will give this a go now, wish me luck

---

### Post by gazj on 2006-05-15
ok that worked :), apart from i had to add the switch -R to make it apply to all subfolders, only one little snag left, i need it to create folders and files with write access to the group share at the moment i only have read and execute under group

Thanks again

---

### Post by ametade on 2006-05-16
[QUOTE=gazj]ok that worked :), apart from i had to add the switch -R to make it apply to all subfolders, only one little snag left, i need it to create folders and files with write access to the group share at the moment i only have read and execute under group

Thanks again[/QUOTE]

I'm glad it worked. For more information on linux filesystem permission check the following article:

[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

