---
title: "How to recover a deleted user account"
date: 2012-11-05
forum: Desktop Environments
---

### Post by vcell on 2012-11-05
A user account was deleted. I just want to restore the account. I have searched this forum and various others, and all I find are solutions when specific conditions exist (e.g. clean install, partition, etc.) None of that applies here. A user's account was deleted using System Settings > User Accounts and I would like to restore it. No files were deleted.

Is there a way to restore the account with it's original settings and files? If so, what must I do? After 2 hours of trying on my own, any assistance is greatly appreciated.

---

### Post by moshuptrail on 2012-11-05
When you say no files were deleted are you saying that the user's home directory and all subdirectories still exist in /home?

---

### Post by vcell on 2012-11-05
Yes. And thanks for the timely response.

---

### Post by mparillo on 2012-11-06
Maybe I am missing something here (I am NOT a system administrator), but could you not simply back up the entire Home path (including 'hidden' files, generally those starting with . (in my case, those are .cache, .config, .dbus, etc. )). Then create the user account from scratch, and slam the files back down?

The only problem I anticipate would be that the permissions would be tied to the old owner, so you might need grant the 'new' user read access to them all, so the 'new' user can create copies under new ownership.

What am I missing?

---

### Post by 28c64 on 2012-11-06
This may help..

[http://www.tuxradar.com/answers/681](http://www.tuxradar.com/answers/681)

---

### Post by black veils on 2012-11-08
> **mparillo said:**
> Maybe I am missing something here (I am NOT a system administrator), but could you not simply back up the entire Home path (including 'hidden' files, generally those starting with . (in my case, those are .cache, .config, .dbus, etc. )). Then create the user account from scratch, and slam the files back down?

The only problem I anticipate would be that the permissions would be tied to the old owner, so you might need grant the 'new' user read access to them all, so the 'new' user can create copies under new ownership.

What am I missing?

something similar would be to backup the personal files within that user account folder. then backup settings for specific applications like web browser, email and messenger, find those in the user account directory by pressing Ctrl + H to show hidden folders. an app folder which doesnt show, may be in .config or .kde etc. copy-paste all these to a usb stick or burn to data cd/dvd.

create your new account and paste those folders back in.

---

### Post by grahammechanical on 2012-11-08
Are you able to re-create that account with **exactly** the same user name and password? If so, then it should be all you need to do.

I have my home folder on a separate /home partition. I can re-install Ubuntu or fresh install into the / partition. If I set up exacty the same user name and password then I get access to the home folder as if nothing has changed. I also have a second user and the home folder for that user remains unchanged and all I need to do is add the second user in User Accounts but the user name and password must be the same. Otherwise you get a third user.

Regards.

---

### Post by Mr_JMM on 2012-11-08
As grahammechanical above said. The only thing I can add is that if you get any issues with permissions etc after (you shouldn't, it works 99% of the time) you can run
```
sudo chown -R [yourgroup]:[youruser] /home/[youruser]
```
e.g. ```
sudo chown -R jimmy:jimmy /home/jimmy
```

but to be honest, the only time that grahammechanical's quick and easy suggestion hasn't worked for me was a clean install of a different distro.

To recreate the user you can use either GUI (search "user" in apps) or terminal using either useradd or adduser, pending your preference. If necessary you might need to re-add the "new" user to the sudoers list.

---

