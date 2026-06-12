---
title: "GDM and authorization file"
date: 2006-09-27
forum: Desktop Environments
---

### Post by bcbroom on 2006-09-27
I've been running Ubuntu for a couple of weeks now, and have liked what I've seen.  Then yesterday I was unable to log in, and have not been able to since.

The exact error I'm (and apparently others) am getting is
GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator

Here is what I have done

I can log in using the recovery mode

verified i have space on the drive
/home is not a seperate partition, / is at 18% usage with 18G free

checked ownership of home
chown username /home/username
chown username:username /home/username (with my real username)

Fiddled with permissions on /home/username
I've tried 600, 644, 664, 755 with no change. If they are set too high then it complains about permissions on /home/user/.dmrc which need to be 644, so I set that one specifically after changing /home/username

I have deleted the .ICEauthority file from /home/username. There is no .Xauthority file there.

I have verified that username is the owner of /home/username, and just to be sure did
chown username:username /home/username

All of the other threads I've read here seemed to be fixed by one of these suggestions, but at this point I'm stumped.  I really don't want to have to reinstall this, it took me the better part of a week to get the packages installed the way I wanted them.
Any ideas?

---

### Post by palle2000 on 2006-11-22
I have the same problem after I have upgraded to 6.10 via network.
Someone any solution??

---

