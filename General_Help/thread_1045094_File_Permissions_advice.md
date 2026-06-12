---
title: "File Permissions advice"
date: 2009-01-20
forum: General Help
---

### Post by CaesarLike on 2009-01-20
HI there.

Okay I need some help with file and directory permissions.

I have 2 users - User1 & User2.  And a group called "sharez", which both users have as a supplementary group.

User1 has a directory called "Access" in his home directory.  This directory is owned by User1 & the sharez group.  The directory has permissions of 660.

My problem is that no matter what file permissions I give a file, User 2 can delete any file in the directory, even files where user1 is the owner and group owner.  So if I had a file with owner and permissions of:

-rw------- User1 User1 File1

User2 can still delete the file.

Is this due to the directory having group permissions of 6?  So that even though the file is not owned by the sharez group, because the directory is owned by the sharez group, any member of that group can delete files irrespective of the actual file permissions?  Or is it due to the fact that both User1 & User2 are in the sharez group, and this over-rides any other group ownership where these users own a file?


So my question is this.  What is the point of file permissions if all I really end up with is either group members can delete everything or nothing?  How do I set up the directory / file permissions to allow for group members to be able to modify the files for their group, but not other groups?

---

### Post by cmnorton on 2009-01-20
Is the directory set drwx-r-x-r-x or drwxrwxrwx. I did not think a user could cd to a directory that was not marked with x privs.

user2 can delete the file, because the file is marked group rw.

---

### Post by CaesarLike on 2009-01-20
sorry, yes your right, it should have been drwxrwxr-x.

As for the file being marked group rw, this appears to have no function in my Ubuntu.  If I have a directory where the group is rw, then the group can delete literally anything in the folder, irrespective of any file perms and or ownership.  If I have the directory as r-x, then if if the file has group permissions of rw, the group members cannot delete the file.

Here is an example:  The directory perms are:

drwxr-xr-x 2 User1 User1       4096 2009-01-20 21:21 Access

and the file perms are:

-rw-rw-r-- 1 User1 sharez 29 2009-01-06 18:12 file1

Yet even with User2 being in the sharez group, it cannot delete the file.

rm: cannot remove `file1': Permission denied


If I change the directory to the following:

drwxr-xr-x 2 User1 sharez 4096 2009-01-20 21:21 Access

Again, User2 cannot delete the file.

---

### Post by cmnorton on 2009-01-20
If you mark a file 644 then, group can only read it.

---

### Post by 73ckn797 on 2009-01-20
See if this info will help out:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by CaesarLike on 2009-01-20
True, but in this case the file was marked 664, so therefore if file permissions apply the group should have been able to delete the file, but could not.

Now if I change the directory to this permission:

drwx-rwx-r-x 2 User1 sharez 4096 2009-01-20 21:21 Access

and the file to this:

-rw-r--r-- 1 User1 User1 29 2009-01-06 18:12 file1

then have User2 rm file1 I am asked:

rm: remove write-protected regular file `file1'? 

and if I say Y then the file is deleted.


73ckn797, thanks for the link.  According to that link for directory permissions -

> write restricts or allows creating new files or deleting files in the directory. (Caution: write access for a directory allows deleting of files in the directory even if the user does not have write permissions for the file!

So clearly the above example is right.  So then my issue is this.  Why cannot User2 delete a file in User1 home directory when the file has group write perms, unless the directory also has write perms?  Or to put it another way, how do I have multiple users access and modify files if the group access will not work without allowing everyone to have write access to a folder?  So if my folder perms are say 755, how do I allow others to access my files since group perms seem to be ignored?  My understanding of the linux file perms system is that it is the file's perms that determine if the file itself can be opened, changed, and deleted by users or groups.

---

### Post by CaesarLike on 2009-01-20
So, anyone have any suggestions for this problem?  So far, the best I can make Ubuntu do is to allow for edit of group owned files, but not create or delete in a directory without group write permissions.  However, if I give the directory group write permissions, then any member of the group can delete any file in the directory irrespective of file permissions.  In other words, for me at least, Ubuntu works pretty much like windows in this respect.  And I thought linux was supposed to be better than this??

---

### Post by cmnorton on 2009-01-20
Is it possible to look at this problem differently? What would happen if you made the directory root read, let user1 and user2 work with these files in their own sandboxes, and then have a root script bring changes back at night?

---

### Post by CaesarLike on 2009-01-20
Thanks cmn, but doesn't the fact that such an approach be used show that the linux file permissions system is not as flexible as it claims?  I thought the purpose of file permissions was to be able to control who can do what for each and every file separately.  But if directory permissions are then going to override a file's own permissions, then I wonder what is the point of having file permissions at all?  True, the file permissions do work to some limited extent, but by no means do they allow for a finer control over file access.

---

### Post by CaesarLike on 2009-01-20
Maybe I have found the problem with the group write permissions for a directory allowing any user to delete files.

This page for installing a HDD:
[https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point]("https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point")

shows this in the instructions:

>   sudo chgrp plugdev /media/mynewdrive
  sudo chmod g+w /media/mynewdrive
  sudo chmod +t /media/mynewdrive

The last "chmod +t" adds the sticky bit, so that people can only delete their own files and sub-directories in a directory, even if they have write permissions to it (see man chmod).

I tried using the sticky bit on the files but this did not work, so it seems that the sticky bit has to be set on the directory itself.

---

