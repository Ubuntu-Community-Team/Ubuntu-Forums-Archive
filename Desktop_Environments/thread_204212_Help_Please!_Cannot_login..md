---
title: "Help Please! Cannot login."
date: 2006-06-26
forum: Desktop Environments
---

### Post by jason.trier on 2006-06-26
I was changing the permissions (it seems I did so incorrectly, through THUNAR) of user folders in /home, so each user could not see the other's files. After doing this, all XFCE sessions shut themselves down. I restarted and now X will not start, nor can I log in as any other user than root. Attempt to login gives an error "cannot cd to /home/$user".

It seems I had changed the permissions to drwx------. I chmodded to 777 and they are at the following now:

root@box:/mnt/hda1/home# ls -lt
drwxrwxrwx 115 1000 4096 Jun 26 15:54 jason
drwxrwxrwx  11  1003 4096 Jun 26 15:54 aja
drwxrwxrwx  27  1002 4096 Jun 26 15:54 josh
drwxrwxrwx    2   dsl   4096 Jun 26 15:54 tweaker

I rebooted and still cannot login as any other user than root. Any help would be much appreciated!

---

### Post by scxtt on 2006-06-26
try a:
[indent]chown jason /home/jason; chgrp users /home/jason[/indent]
and see if jason can log in ...

[color=red]note[/color]: i don't know what group jason was in before, so if you do, switch that out w/ "users" ...

it looks like the user/group designations are gone:

```
scxtt@$hostname [/home]
:> ls -lt
total 4
drwxr-xr-x 39 scxtt scxtt 4096 2006-06-26 16:34 scxtt
```

---

### Post by GarlicFish on 2006-06-26
I just took a look at my permissions
cd /
drwxr-xr-x   4 root   root    4096 2005-08-02 20:23 home
cd /home
drwxr-xr-x 50 blah blah 4096 2006-06-26 21:23 blah
make sure you ripple ownership and permisisons to the subdirectories

chmod -r 755 /home/blah
chown -r blah:blah /home/blah

that should sort out any mess
if that doesn't work, try manually starting X and see what happens.

---

### Post by jason.trier on 2006-06-26
Didn't work :(. The permissions took and the groups are set correctly. Still can only login at tty as root. Attempting to login as other users results in "can't cd to /home/$user".

---

### Post by jason.trier on 2006-06-26
OK, so I ran "startx" at the root terminal and successfully started XFCE. In a terminal window I type:

```
root@localhost:~# su jason
No shell
```

Any ideas?

p.s. Cannot run users-admin either due to wrong password from root user???

---

### Post by scxtt on 2006-06-26
i'd recreate the user accounts ... i think you can do that w/o deleting their /home directories (back em up just to be sure) ... or try to make a new user "useradd TestUser" just to see if they can login fine ...

i don't know what you did (not even really faulting you), but it seems like something happeded aside from a few folder permission changes ...

---

### Post by jason.trier on 2006-06-26
[QUOTE=scxtt]i'd recreate the user accounts ... i think you can do that w/o deleting their /home directories (back em up just to be sure) ... or try to make a new user "useradd TestUser" just to see if they can login fine ...

i don't know what you did (not even really faulting you), but it seems like something happeded aside from a few folder permission changes ...[/QUOTE]

It's possible.. but anyways my brother came down and decided chmodding the whole drive to the same permission should fix the problem. So now I have to backup and reinstall.

Which brings me to this question- is there a way to reinstall that won't destroy my /home data (one partition-install with a swap partition)?

---

### Post by scxtt on 2006-06-26
i think the only way you can get what you're looking for is if you ALREADY have a separate /home partition {won't be touched on a reinstall} ... so unless you've already set it up that way, i think you're SOL {aside from a backup scheme} ...

as root, you should have been able to go to System --> Administration --> Users & Groups to fix most problems for each user (the shell problem) ...

there's really no reason root can't chmod/chown/chgrp and fix things up w/ "Users & Groups" to get things fixed -- there must be a deeper problem ...

---

