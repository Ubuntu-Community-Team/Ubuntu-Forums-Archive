---
title: "Simple clean install question"
date: 2008-12-26
forum: General Help
---

### Post by 3pinner on 2008-12-26
Or maybe not!
I have a hard disk divided up into 3 partitions / swap /home.
I have two accounts, admin(Lets call it Bob), and user (lets call it myaccount)
The /home folder has Bob and myaccount folders.

I did a clean install on the / partition. no problems.
I created one account as part of the logon process and named it Bob (just like the old installation).
When I opened Intrepid for the first time, I had full access to the Bob folder I left on /home; but could not create a user to access the myaccount folder.
I posted a question in another thread and solved the problem.

MY NEW QUESTION:
 How could I have avoided the problem in the first place? 
Did I miss an opportunity to create a second account during the install?
What's the best way to handle this in the future?

I really like the idea of having seperate partitions so I can install an updated OS, and not lose any of my settings.

Thanks!

---

### Post by kindlinux on 2008-12-26
> When I opened Intrepid for the first time, I had full access to the Bob folder I left on /home; but could not create a user to access the myaccount folder.

check the permissions...
Am sure ubuntu has a perssion manager...

---

### Post by 3pinner on 2008-12-26
Users and groups was no help. I ended up using the following commands to corrrect it:

Code:
sudo adduser --no-create-home myname
sudo chown -R myname:myname
sudo chmod 755 /home
sudo chmod 770 /home/myname
After that log in as your old user "myname".

My question is:
For a clean install of the latest upgrade, is this the only way to go to recreate users, so they have access to their folders in the /home partition?

---

### Post by 3pinner on 2008-12-27
Or is there a way do do it during install?

---

### Post by 3pinner on 2008-12-27
anyone?
thanks!

---

