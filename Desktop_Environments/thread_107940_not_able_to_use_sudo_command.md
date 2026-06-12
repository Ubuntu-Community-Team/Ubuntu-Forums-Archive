---
title: "not able to use sudo command"
date: 2005-12-24
forum: Desktop Environments
---

### Post by heart_reaver on 2005-12-24
I m not able use sudo

Example

-----------------------------------------------------------------
anu@amnesty:~$ sudo apt-get apollon
anu is not in the sudoers file.  This incident will be reported.

---

### Post by kaamos on 2005-12-24
When booting the machine, choose "Recovery mode" in grubs menu. Then you are logged in as root. Enter the command```
visudo
```And add this to the end of the file.> anu ALL=(ALL) ALL
Save the file. Then reboot with "shutdown -r now" and log in normally. You should now be able to use sudo

Hope this helps!

---

### Post by gsdefender on 2005-12-24
The way shown above is OK, but shows a potential security breach, where anyone can do anything. Taking into account that sudo often requires patches, I would do (and, actually, do ;-)) this way:

Host_Alias HERE=amnesty
User_Alias PRIVILEGED=anu

Cmnd_Alias ADMIN=/usr/bin/apt

PRIVILEGED HERE=ADMIN, NOPASSWD: ADMIN

You can, obviously, set as many aliases to hosts, users and groups of commands as you wish. The effect is the same.

---

### Post by kaamos on 2005-12-24
I wasn't aware of that, could you please explain how this opens the possibility of a breach? Should one not assing usernames in the file? Never heard of this. :o

---

### Post by GTvulse on 2005-12-24
[QUOTE=heart_reaver]I m not able use sudo

Example

-----------------------------------------------------------------
anu@amnesty:~$ sudo apt-get apollon
anu is not in the sudoers file.  This incident will be reported.[/QUOTE]

I bet this is not the first user you created in the system. While the advice you have received is fine, the first thing to check is if your user account is included in the **admin** group. That group has sudo administration privileges in a default ubuntu installation. If your account doesn't belong to that group the solution is simple; boot up in maintenance mode as already indicated. Type "vigr", add your username to the admin group, save and type "exit", the system will continue its normal booting process changing from single-user to multiuser and when you log into your account, you'll have administration privileges with sudo.

No need to reboot, nor to play with the sudoers file until you have taken the time to read its manual page (believe me, it is worth it, a bad sudoers file can leave you out of an otherwise perfectly working system).

---

### Post by gsdefender on 2005-12-24
> I wasn't aware of that, could you please explain how this opens the possibility of a breach? Should one not assing usernames in the file? Never heard of this. :o

The problem lies in that (ALL)=(ALL). If you think about it, it's like doing chmod +s on every executable. As sudo has been subject to several problems, both on remote and locale side, in recent times (I remember nights tinkering with updates on Slackware), it's preferable to avoid that. 

Using the way I proposed, you can limit the effect of a security breach to the system that's running sudo and to the executables you have specified. It's not a cure, but sort of a barrier. ;-)

---

### Post by heart_reaver on 2005-12-24
[QUOTE=dradul]I bet this is not the first user you created in the system. While the advice you have received is fine, the first thing to check is if your user account is included in the **admin** group. That group has sudo administration privileges in a default ubuntu installation. If your account doesn't belong to that group the solution is simple; boot up in maintenance mode as already indicated. Type "vigr", add your username to the admin group, save and type "exit", the system will continue its normal booting process changing from single-user to multiuser and when you log into your account, you'll have administration privileges with sudo.

No need to reboot, nor to play with the sudoers file until you have taken the time to read its manual page (believe me, it is worth it, a bad sudoers file can leave you out of an otherwise perfectly working system).[/QUOTE]


That is my first and only user

Thanks for all help :p

---

### Post by ardchoille on 2006-07-25
> **gsdefender said:**
> The problem lies in that (ALL)=(ALL). If you think about it, it's like doing chmod +s on every executable. As sudo has been subject to several problems, both on remote and locale side, in recent times (I remember nights tinkering with updates on Slackware), it's preferable to avoid that. 

Using the way I proposed, you can limit the effect of a security breach to the system that's running sudo and to the executables you have specified. It's not a cure, but sort of a barrier. ;-)

I have 6 users on my machine, I am the only one in sudoers. I always add myself to the wheel group and then do this on a new machine:
```

sudo chown root:wheel /bin/su && sudo chmod 4750 /bin/su

```
This makes it so that anyone else on the system gets a permission denied error when they try to "su" (an old trick I learned from a veteran Red Hat employee) and they get a denied error when they try to use sudo.

Forgive me, but I don't see a problem with the sudoers set up. Can you explain more?

---

### Post by Nelion Shevanas on 2008-06-18
^^" solved

---

