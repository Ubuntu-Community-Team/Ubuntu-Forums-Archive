---
title: "Ubuntu home folder is wiped clean when changed owner of home folder"
date: 2012-11-29
forum: Desktop Environments
---

### Post by rohitlambi on 2012-11-29
Ubuntu home folder is wiped clean when changed the owner of home folder  from root to the current logged in user.

I rebooted my Ubuntu 10.04 LTS and when i entered my credentials a pop up appeared saying

"Could not update ICEauthority file /home/user/.ICEauthority"

After going forward with clicking ok, a blank screen appeared.

I searched for possible solutions for this problem i got one which said: check the owner of home folder and if its not the same as logged in user then change it to one.

So, I executed following command and rebooted the system
sudo chown -R user:user home

After that i was able to properly login but i could'nt see any of my files; it was like a fresh ubuntu installation.

Please help me getting my data back it was very important :(

---

### Post by SlugSlug on 2012-11-29
Can you please paste the output of 

```
whoami
```

and

```
ls -l /home
```

chmod won't delete files. (rm would..?)

---

### Post by rohitlambi on 2012-11-29
hi, thank you for replying.

yes, chmod should not delete files but I can't see any of my files; 
now my /home folder is like it is when you install fresh ubuntu

Here is the output of the above commands you asked for:

user@lemon-desktop:~$ whoami
user

user@lemon-desktop:~$ ls -l /home
total 4
drwxr-xr-x 24 user user 4096 2012-11-29 10:57 user


user@lemon-desktop:~$ ls -l /home/user
total 36
-rw-r--r-- 1 user user  594 2012-11-29 22:30 cron_daily_task_log.log
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Desktop
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Documents
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Downloads
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Music
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Pictures
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Public
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Templates
drwxr-xr-x 2 user user 4096 2012-11-28 19:26 Videos

ls -l /home/user shows total 36; this is including hidden files

---

### Post by SlugSlug on 2012-11-29
humm nt sure, looking at the dates it seems they where all created yesterday (not good )

---

