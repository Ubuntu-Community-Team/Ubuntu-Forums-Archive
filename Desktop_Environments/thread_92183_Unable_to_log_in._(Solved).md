---
title: "Unable to log in. (Solved)"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Cyril on 2005-11-18
When I try to log in I get the following error:

"GDM could not write to your authorization file.  This could mean that you are out of disk space or your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator."

I am very certain I have sufficient disk space.

I do not know if this is relevant but owner of /home is root.  Permissions are 755.  Owner of /home/cyril is cyril.(cyril is the account I am trying to log into.) Permissions are 755.

I tried creating another account but I get the same error when trying to log in with that account.

Please advise.

---

### Post by adwait on 2005-11-19
What are the permissions of ~/.Xauthority?

---

### Post by Cyril on 2005-11-19
Permissions for ~/.Xauthority are 600.
I've tried changing to 777 but I still get the same error.

---

### Post by invalid on 2005-11-19
I had a problem once with ~/.ICEauthority
Make sure this too has enough permissions.

Cb

---

### Post by Cyril on 2005-11-19
Permissions of ~/.ICEauthority is 600 as well.  Is that what it's supposed to be?

---

### Post by invalid on 2005-11-19
As long as you own the file, this should be correct.

Cb

---

### Post by Cyril on 2005-11-19
Just before this problem occured I was having problems creating a directory in my home directory.
I tried mkdir abc and I got this error saying it could not be created because I have insufficient disk space but I have a few gigabytes of free space.  I thought this problem might go away if I reboot so i tried it.  Then I couldn't log in.

Ideas anyone?

---

### Post by Cyril on 2005-11-19
Desperate! Please help.

---

### Post by angkor on 2005-11-19
Try moving both files to .Iceauthority_bak and .Xauthority_bak. Both files should be replaced by new ones. 

If it doesn't work you can always put them back, no harm in trying.

---

### Post by metoo on 2005-11-19
Boot into recovery mode
log in (text mode)
df -h gives you the hd usage

Just to be sure, that you have the free space on the right partitions...

In case you have mc installed, it comes quiet handy if you have to delete some files in text/console mode.

---

### Post by Cyril on 2005-11-19
Ok, finally figured it out. A lot of stuff I deleted were in hidden folders and so were hidden in my .Trash folder as well.  So I had a huge trash folder and didn't know about it.

Boy do I feel dumb.

Thanks to all that helped.

---

