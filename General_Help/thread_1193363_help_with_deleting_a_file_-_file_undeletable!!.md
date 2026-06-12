---
title: "help with deleting a file - file undeletable!!"
date: 2009-06-21
forum: General Help
---

### Post by mintyhippo on 2009-06-21
hi, i have a problem with a particular file on my windows partition. I am trying to completely erase mozilla firefox from my system manually since the uninstaller did not work. so far this is what i have done (in windows);

- I have deleted everything related to firefox in the application data directory (including the profile .lock files)
- ran the the control panel uninstall for firefox 
- deleted all contents in side the directory  c:\program files\mozilla firefox 
- and restarted my computer
        
*all i have left is the directory c:\program files\mozilla firefox.

 This directory will not delete despite everycommand i have used in the command prompt as well as Dosbox. both of which tell me that the file is in use. I know it is not in use because the process firefox.exe is not running in the taskmanager and because all contents inside the folder are empty. I have restarted my computer to make sure that no process is using that folder and still it will not delete.

now since all attempts within windows failed I went on to try deleting this directory from the outside using my ubuntu partition. 
heres what i have tried in ubuntu ;

-went inside windows file system, located and attempted to delete the file (did not work)
-went to terminal used "cd" to navigate to directory and to delete (did not work)
-became root user and tried again (did not work) *error said the file was read only*
-attempted to change permissions of the file using "chmod 777 "mozilla firefox" and still did nothing to change the permissions.
 heres what i input;
 [FONT=Impact] root@user-laptop:/media/disk/Program Files# chmod 777 "mozilla firefox[/FONT]" 
 heres the output;
[FONT=Impact]  chmod: changing permissions of `mozilla firefox': Read-only file system[/FONT]

I am sort of running out of ideas how to delete this file...

I think the problem stemmed from my laptop intermittenly powering off because the jack for the charge cable is unreliable. maybe this somehow currupted the file idk. all i want to do is wipe out all traces of firefox and reinstall so it can start working correctly again. this whole ordeal started when firefox was acting strange. I had to click out of the window and click back into the windows in order to use its GUI . i could'nt click on links after searching something in google, could not exit and couldn't even press "back" without changeing windows and coming back to the firefox window. very frustrating...

- anyway thanx for reading my problem and sry that my first ubuntu forum post is a windows related one. regardless, any help would be greatly appreciated.

**additionally i would like to say that i would prefer not installing a program to delete this ONE file. i know in windows they have some software that supposedly deletes anything but i would prefer not to bloat windows anymore than it already is. and i would also prefer to keep my ubuntu partition clean.**

---

### Post by paperplate9 on 2009-06-21
Well when you're under Ubuntu, you've mounted the filesystem readonly, so of course you won't be able to delete.

If you think your drive is corrupt, run a fsck on it.

Since this is an Ubuntu forum, I won't get into windows-related stuff, but mount the filesystem with write permissions. What fs type is the partition? NTFS?

---

### Post by The-Don on 2009-06-21
Confused - you using Linux or Windows? (as you mentioned c:\program files\).

In Linux:
```
sudo aptitude remove firefox
sudo aptitude clean
sudo aptitude autoclean
apt-get --purge remove firefox
```
Worked for me (a Google Chrome user).

---

### Post by freebeer on 2009-06-21
Looks like the file (directory) was given the system attribute.  Try using the "attrib" command in Windows' command line.

```

attrib -S c:\program files\mozilla firefox

```

This should remove the system flag on the file and you should be able to delete it now.  (assuming it is not Read-only, too)

you can change the read-only bit with

```

attrib -R c:\program files\mozilla firefox

```

You may need to do this from an account with Administrator privileges.

---

### Post by mintyhippo on 2009-06-21
thanx freebeer, 
 
"attrib -S c:\program files\mozilla firefox"
 
 was exactly what i needed.

---

### Post by paperplate9 on 2009-06-21
> **mintyhippo said:**
> 
 [FONT=Impact] root@user-laptop:/media/disk/Program Files# chmod 777 "mozilla firefox[/FONT]" 
 heres the output;
[FONT=Impact]  chmod: changing permissions of `mozilla firefox': Read-only file system[/FONT]


...as stated.

---

### Post by Johnny B on 2009-06-21
> **paperplate9 said:**
> ...as stated.

looks like you mounted that drive/partition as read only.
try installing ntfs-3g
```
# sudo apt-get install ntfs-3g ntfs-config
```
then unmount and mount again

---

### Post by freebeer on 2009-06-21
Glad I could help.  Windows' command line tools aren't nearly as robust as Linux's but they're still there for such pesky little tasks.  :D

---

