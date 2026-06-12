---
title: "Accedently chmod -R --no-preserve-root 0 /"
date: 2009-04-30
forum: General Help
---

### Post by mulder_edu on 2009-04-30
I was trying to wipe out the permissions of a specific user account from / up (I typed "chmod -R --no-preserve-root 0 / username"), but it thought that the username was a directory and couldn't locate it, then it just wiped out my permissions to everything logged on as root user.  I still have read and write access using webmin, but I'm not sure what file to edit to undo what I just did.  Any suggestions?

---

### Post by wirelessmonkey on 2009-04-30
I don't think that there is any file you can edit to fix this, you've basically wiped permissions across the directory tree... this is a backup and reinstall situation I'm afraid.

---

### Post by mulder_edu on 2009-04-30
Are you sure there isn't anyway to manually edit the permissions of a file or directory without chmod?

---

### Post by wirelessmonkey on 2009-04-30
Sure? No.

But unless you're using AppArmor or SELinux, chmod is the only way I know of.
Hopefully someone else will know better.

Best of Luck.

---

### Post by bodhi.zazen on 2009-04-30
I am not aware of editing a file's permissions with anything but chmod.

Restoring from backup or saving yoru data and re-installing are both much much faster.

In order to restore your permissions you would need to know the ownership and permissions of each and every file and directory in / , or at least the system files at a minimum.

How long do you think it will take you to manually change ownership and permissions of all these files ? I have seen people try to do this and it usually goes on for several days, and ends with a re-installation. I do not know anyone who has manually reset all these files successfully, and most of the experienced users do not try.

Making a back up and reinstalling will probably take less time.

---

### Post by mulder_edu on 2009-05-08
Ha! we got it working, mostly. So, ofcourse we didnt have backups. (things like this never happen when you have backups.) To fix we just booted w/ a live cd and chmod everything, and have gone through by hand trying to restore files back to their default permissions. But now we have run into another problem. (yes, very likely related.), I cant seem to get a FTP server working. I have tried vsftpd, proftpd and pure-ftpd, I know that the ports are all open, because proftpd (the original one that was on the box) was working fine right before this whole mess. but when I try to connect with my client, it gives messages like "server unexpectedly closed network connection.". I just finished exhausting all the options that I can think of with pure-ftpd, but it is still installed and running. i am running it with anonymous activated, and I still cant connect/keep a connection.  Any ideas? maybe just a file or folder that I didnt change permissions on correctly?

---

