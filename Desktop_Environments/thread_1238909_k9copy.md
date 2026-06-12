---
title: "k9copy"
date: 2009-08-12
forum: Desktop Environments
---

### Post by andrea000 on 2009-08-12
I installed k9copy but i cant seem to get it to work
the way it should or is there a better software to do
the same thing here is what i get when i run it in the
terminal.

Error: Can not create link from "/home/me/.kde/cache-me-desktop" to "/var/tmp/kdecache-me"
Error: Can not create link from "/home/me/.kde/cache-me-desktop" to "/var/tmp/kdecache-meVXGCa9"
trying to create local folder /home/me/.kde/cache-me-desktop: Permission denied
trying to create local folder /home/me/.kde/cache-me-desktop: Permission denied
trying to create local folder /home/me/.kde/cache-me-desktop: Permission denied
trying to create local folder /home/me/.kde/cache-me-desktop: Permission denied
Error: Can not create link from "/home/me/.kde/tmp-me-desktop" to "/tmp/kde-me"
Error: Can not create link from "/home/me/.kde/tmp-me-desktop" to "/tmp/kde-metaTFU7"
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
k9copy(9062): Failed to lock file "/home/me/.kde/cache-me-desktop/kpc/kde-icon-cache.lock" , last result = 2 
k9copy(9062): Couldn't create index file "/home/me/.kde/cache-me-desktop/kpc/kde-icon-cache.index" 
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
trying to create local folder /home/me/.kde/tmp-me-desktop: Permission denied
QFile::remove: Empty or null file name

---

### Post by andrea000 on 2009-08-13
ok this is day two of trying to fix k9copy with no luck
i am done with it for good.Would anyone know of another
piece of software that will do what k9copy is supposed
to do.

thank you

---

### Post by Bigtime_Scrub on 2009-08-13
What are you trying to use k9copy for? Fair use DVD copies or something else? For fair use DVD copies, it is really the only native Linux option.

How were you installing it?

Unfortunately if you want to make DVD back ups and you do NOT want k9copy then the only real suggestion I have would be Wine + DVDshrink.

---

### Post by andrea000 on 2009-08-13
I'm just wanting to make a copy if i wanted to remove the copy protection i could just install
dvd fab in wine and do that it's easy enough to remove that i just want a exact copy with the
menus in there.Synaptic is how i'm installing it.

---

### Post by bboston7 on 2009-08-13
Did it work at some point?

I would try re-installing with
```
sudo apt-get purge k9copy
sudo apt-get install k9copy
```
this will remove all configuration files as well, just encase something got messed up.  

Also, it seems that most of your errors are permission errors.  Try 
```
sudo chown me /home/me/.kde/tmp-me-desktop
```

---

### Post by andrea000 on 2009-08-13
no this is the first time i have used k9copy i ripped
my dvd before but i had to reinstall a few days ago
and lost the avi's of them now i do not want to make
the same mistake again so i am going to make dvd's
backup's of them.

---

### Post by yabbadabbadont on 2009-08-13
Check the permissions on your /tmp directory.  The sticky bit should be enabled, which allows users to create and remove files/directories in /tmp.  Here is what mine looks like as an example:
```
/home/daffy $ ls -ld /tmp
drwxrwxrwt 8 root root 4096 2009-08-13 19:56 /tmp

```
If the 't' is missing from the permissions on yours, then that is most likely the problem.

---

### Post by andrea000 on 2009-08-13
ok when i run this command sudo chown me /home/me/.kde/tmp-me-desktop
i get this chown: cannot access `/home/me/.kde/tmp-me-desktop': No such file or directory
I'm still not sure what i'm doing wrong

---

### Post by yabbadabbadont on 2009-08-13
Did you check the permissions on your /tmp directory?

Edit: also, what are the permissions on your .kde directory?  i.e. what is the output of "ls -ld ~/.kde"

---

### Post by andrea000 on 2009-08-13
They were both root i changed them to me but it did not help
would you know anything about xdvdshrink i am not looking to
shrink the dvd but it may be something i can use.

---

### Post by andrea000 on 2009-08-14
This is the error i get when i try to
copy a dvd with k9copy it says something
about a full hard drive but my hard drive
is no were full 

Unable to save bookmarks in /home/me/.kde/share/apps/kfileplaces/bookmarks.xml. Reported error was: Insufficient permissions in target directory.. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

---

### Post by andrea000 on 2009-08-14
ok i have it working i you have to have the
medibuntu repositories enabled for it to work
and install libdvdcss2 for it to work.

thanks you all for your help

---

