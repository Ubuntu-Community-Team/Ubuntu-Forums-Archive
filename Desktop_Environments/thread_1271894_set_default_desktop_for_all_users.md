---
title: "set default desktop for all users"
date: 2009-09-21
forum: Desktop Environments
---

### Post by felixvah on 2009-09-21
I've ubuntu 9.04 on a virtual box.  Is there possible to set a default windows desktop for all users?  Once I configure the very first desktop and settings, I want to apply to all users that logon to the same PC.  I don't like logon to individual account and re-configure all settings, desktop, screen saver and etc. again. 

Another question was if I log on as a user without administration, how would I sudo with a different users with administration?  I've tried sudo su - but when I type in the password, it didn't allow me to change.  Can someone please help.  Thank you,

---

### Post by arrange on 2009-09-22
It should be possible to copy all settings from one account to another though I have not tested it thoroughly.

Create an account using the usual *Users and Groups* option. Let's say we have 2 users then: **original** and **copycat**. First copy the contents of the original home direcory and change its ownership ```
sudo cp -rT /home/original/ /home/copycat/
sudo chown -R copycat:copycat /home/copycat/
```Depending on your initial setting of the *original* you may have some references to that user in the profile; check that```
sudo grep -lIR '\/home\/original' /home/copycat 2> /dev/null
```If you see any files that contain a reference to */home/original*, change the reference manually to */home/copycat* or run ```
sudo -i
grep -lIR '\/home\/original' /home/copycat 2> /dev/null | while read F; do sed -i 's:\/home\/original:\/home\/copycat:g' "$F"; done
```

When I was testing this, the *copycat* account was identical to the original including FF, TB and Evolution profiles. The only thing that seemed broken was positioning and scaling of icons on the destop. Actually, I'm writing this from a copycat account :)

Report back how you worked it out.

ad 2) You can't *sudo* with a user who is not in the *admin* group (not an administrator).

---

### Post by felixvah on 2009-09-22
I'm not able to copy.  Here's my command error:

felix@felix-desktop:~$ sudo cp -rT /home/felix/ /home/mcpl/
cp: cannot stat `/home/felix/.gvfs': Permission denied

---

### Post by arrange on 2009-09-22
As long as it has copied all the other files, I think you can ignore this error - for more details see for example [this bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361").

---

