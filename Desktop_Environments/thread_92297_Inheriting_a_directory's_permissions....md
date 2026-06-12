---
title: "Inheriting a directory's permissions..."
date: 2005-11-19
forum: Desktop Environments
---

### Post by mmcmonster on 2005-11-19
Hi.
  I'm trying to set up a box to give to my brother.  In addition to the usual users in /home, I created a directory there called /home/shared/Photos.  I want that directory (and all subdirectories within) to be a+rw (and execute for the directories, I guess), so that different users can just drop files in there and have the files there viewable to anyone on the computer, and anyone can edit the files as well.
  I tried mucking around a bit and can't figure it out.  Can anyone help me?

Thanks.
MMC

---

### Post by adwait on 2005-11-19
You could put all the users in the same group and then set the permissions to 774.
```
chmod 774 /home/shared/Photos
```

---

### Post by mmcmonster on 2005-11-19
[QUOTE=adwait]You could put all the users in the same group and then set the permissions to 774.
```
chmod 774 /home/shared/Photos
```[/QUOTE]

Actually, I had chmod'ed the directory as 777.  When a different user dragged a file into the directory, it was rwx------.

---

### Post by adwait on 2005-11-19
Wierd...but  from the same account, you could see it as 777?

---

### Post by mmcmonster on 2005-11-19
[QUOTE=adwait]Wierd...but  from the same account, you could see it as 777?[/QUOTE]

Maybe I mis-stated myself.  Here is (an abbreviated version of) my shared Photo directory.  I replaced the user names with user1 and user2.  As you can see, user2 dropped the file "Firefox.desktop" into the directory; the file *did not* inherit the attributes of the directory.  What I want as the exprected behaviour is for the file to be chmod'ed 777 (or at least 666).

```

drwxrwxrwx  39 root    root     4096 2005-11-19 12:23 .
drwxrwxrwx   4 root    root     4096 2005-11-19 09:53 ..
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:07 2004 - 01 - San Antonio
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:06 2004 - 02 - Grenada
-rwx------   1 user2   user2    206 2005-11-19 09:55 Firefox.desktop
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:00 Flowers
-rwxrwxrwx   1 user1   user1    668 2005-09-04 15:50 Sample Pictures.lnk
user1@avalon:/home/shared/Photo$

```

---

### Post by cwaldbieser on 2005-11-20
[QUOTE=mmcmonster]Maybe I mis-stated myself.  Here is (an abbreviated version of) my shared Photo directory.  I replaced the user names with user1 and user2.  As you can see, user2 dropped the file "Firefox.desktop" into the directory; the file *did not* inherit the attributes of the directory.  What I want as the exprected behaviour is for the file to be chmod'ed 777 (or at least 666).

```

drwxrwxrwx  39 root    root     4096 2005-11-19 12:23 .
drwxrwxrwx   4 root    root     4096 2005-11-19 09:53 ..
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:07 2004 - 01 - San Antonio
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:06 2004 - 02 - Grenada
-rwx------   1 user2   user2    206 2005-11-19 09:55 Firefox.desktop
drwxrwxrwx   2 user1   user1    4096 2005-10-22 14:00 Flowers
-rwxrwxrwx   1 user1   user1    668 2005-09-04 15:50 Sample Pictures.lnk
user1@avalon:/home/shared/Photo$

```[/QUOTE]

The permissions on the copied file are not influenced by the permissions of the containing folder.  The permissions are set by the program that creates the file.  When copying a file, this normally means that the copy has the same permissons as the original file.

When someone copies a file to the folder, they should set the permissions so anyone can read them.

---

### Post by mmcmonster on 2005-11-20
[QUOTE=cwaldbieser]The permissions on the copied file are not influenced by the permissions of the containing folder.  The permissions are set by the program that creates the file.  When copying a file, this normally means that the copy has the same permissons as the original file.

When someone copies a file to the folder, they should set the permissions so anyone can read them.[/QUOTE]

No easy, automatic way to do this?  Maybe I can run a shell script each time a person logs on (or off) to chmod everything they own in the share folder?  (Where would I put that sort of script, anyway?)

---

### Post by garyng on 2005-11-20
[QUOTE=mmcmonster]No easy, automatic way to do this?  Maybe I can run a shell script each time a person logs on (or off) to chmod everything they own in the share folder?  (Where would I put that sort of script, anyway?)[/QUOTE]

Make the directory group access right sticky, then all files dropped in there would get this right(and group ownership) and just add those user to this specific group.

mkdir shared
chown me.common shared
chmod 2770 shared

---

