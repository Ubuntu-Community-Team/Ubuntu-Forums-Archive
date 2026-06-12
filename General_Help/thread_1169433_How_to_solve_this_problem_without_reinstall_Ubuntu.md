---
title: "How to solve this problem without reinstall Ubuntu?"
date: 2009-05-25
forum: General Help
---

### Post by csh on 2009-05-25
I log on to Ubuntu 9.04 by using my own administrator account. I tried to create another administrator account. After a new administrator account has been created, the problem occured.

I try to log out, and then log in again with my original administrator account. Then, I tried to run System -> Administration -> Users and groups, an error message "You are not allowed to access the system configuration.".

Then, I log out and log in again by using my new Administrator account, then in System -> Administration -> Users and groups, I cannot unlock it. When I click the unlock button, the user setting hang, and nothing happened.

Why these problems occured? Any ways to solve the problems without reinstalling Ubuntu?

And, please don't ask me the reason for creating another administrator account.

Any replies will be appreciated.

---

### Post by leandromartinez98 on 2009-05-25
First, why would you want a new adminitrator account??? :-P

Seriously, try editing your /etc/group file. This file contains the permisions
for each user. For a user to be an administrator, it must belong to the
groups  "admin" and "adm". You just have to add the user name of your "administrator"
to the lines of these groups, like:

```

adm:x:4:leandro

```

(my username is leandro)

By the way, you can allow any user to administer the system, giving administrator
privileges to it (editing this file or though the GUI). If your idea was to
create another "root" account, I think that makes no sense, you probably created
a normal user named "root" (if that is possible at all), and that is causing
the problems.

By the way, you can edit the /etc/group file from a rescue boot if you cannot
edit them using any of your available accounts.

---

### Post by sisco311 on 2009-05-25
Reboot in Recovery Mode and add your user to the admin group.

details:
[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by csh on 2009-05-25
> **leandromartinez98 said:**
> First, why would you want a new adminitrator account??? :-P

Seriously, try editing your /etc/group file. This file contains the permisions
for each user. For a user to be an administrator, it must belong to the
groups  "admin" and "adm". You just have to add the user name of your "administrator"
to the lines of these groups, like:

```

adm:x:4:leandro

```

(my username is leandro)

By the way, you can allow any user to administer the system, giving administrator
privileges to it (editing this file or though the GUI). If your idea was to
create another "root" account, I think that makes no sense, you probably created
a normal user named "root" (if that is possible at all), and that is causing
the problems.

By the way, you can edit the /etc/group file from a rescue boot if you cannot
edit them using any of your available accounts.

Firstly, thanks for your reply. I create another administrator account because I want to have two administrator account. In case there is any problem with one of my administrator account, I can use another account to do administrative tasks.

For your info, my new account was given 'admin' as the user name. Was this caused the problem? If I cannot use that user name, why don't Ubuntu display a message to tell me?

---

### Post by 3rdalbum on 2009-05-25
> **csh said:**
> For your info, my new account was given 'admin' as the user name. Was this caused the problem?

There's your problem. 'admin' is already the name of a group on your system.

I believe this is mentioned in the Ubuntu 9.04 release notes, and I think I also saw an update being pushed out for this not too long ago. Are you fully up-to-date? In any case, applying the update now might not solve the problem.

Unfortunately I'm not sure how to solve your immediate problem, and I'm hoping someone else will be able to help with a bit of command-line user modification.

But, do you see the irony? You created another administration user in case your original one wouldn't work, but in the process you caused both to not work! It's really not necessary to create another administration user for this circumstance, as it's always possible to log in directly as root on the Recovery Mode terminal.

---

### Post by csh on 2009-05-25
> **3rdalbum said:**
> There's your problem. 'admin' is already the name of a group on your system.

I believe this is mentioned in the Ubuntu 9.04 release notes, and I think I also saw an update being pushed out for this not too long ago. Are you fully up-to-date? In any case, applying the update now might not solve the problem.

Unfortunately I'm not sure how to solve your immediate problem, and I'm hoping someone else will be able to help with a bit of command-line user modification.

But, do you see the irony? You created another administration user in case your original one wouldn't work, but in the process you caused both to not work! It's really not necessary to create another administration user for this circumstance, as it's always possible to log in directly as root on the Recovery Mode terminal.

Ok. It seems like I need to reinstall Ubuntu to solve this problem.

I went to Ubuntu 9.04 release notes site at [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904), and cannot find the word 'admin'.

However, if anybody have the solution, kindly please tell us here so that the other users who done similar things and have the same problem can solve it without reinstallation.

I will post an idea in Ubuntu brainstorm, about alerting and preventing the users from creating an account with user name which was already a system group name.

However, I appreciate everybody who reply in this thread. Thank you and have a nice day.

---

### Post by Iowan on 2009-05-25
If you can boot to recovery mode, you might be able to edit the /etc/passwd (and /etc/shadow files to rename/delete your new admin.  Renaming is messy - as there are probably home directories, etc., but *can* be done.
If recovery mode won't work, you might use something like [tomsrtbt]("http://www.toms.net/rb/") to gain system access.

---

### Post by sisco311 on 2009-05-25
You have to remove the "admin" user. 

First boot in Recovery Mode.

Then backup the /etc/passwd and /etc/shadow files
```
cp /etc/shadow /etc/shadow-backup
cp /etc/passwd /etc/passwd-backup
```
 
Now you can remove the user with:
```
deluser admin
```

The command works for me, but if you wish you can remove the user manually.

For this you have to edit the passwd and shadow files, type:
```
EDITOR=nano vipw
```
This command will open the /etc/passwd file in a text editor.
The file contains a list of user accounts. Search for the line that begins with "admin" and delete it. Save the file and exit(Ctrl+x, y, Enter).

> [noparse]root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
...
[/noparse]**[noparse]admin:x:1001:1001:/home/admin:/bin/bash[/noparse]**
...


Now edit the shadow file:
```
EDITOR=nano vipw -s
```
Once again search for the "admin" line and delete it:
> [noparse]
root:!:14379:0:99999:7:::
daemon:*:14379:0:99999:7:::
...
[/noparse]**[noparse]admin:$be5hYnnV/dk5B9gWGa/k3rrsmXxpqLULZ:14379:0:99999:7:::[/noparse]**
...


Make sure that your primary user is in the admin group, log out and choose to resume a normal boot:
```
adduser YOURUSERNAME admin
#Press Ctrl+D
```

---

### Post by sisco311 on 2009-05-25
Here is the BUG report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305")

You will need to edit the /etc/group file as well.

Back it up:
```
cp /etc/group /etc/group-backup
```

then
```
EDITOR=nano vipw -g
```

Search for the admin line and change back the group id to 113:
> [noparse]admin:x:1001:USERNAME[/noparse]
-->
> [noparse]admin:x:113:USERNAME[/noparse]

NOTE:
```
groupmod -g 113 admin
```
should also work, but manually editing files is always fun :)

NOTE2:
If something goes wrong, you can restore the original files with:
```
cp /etc/passwd-backup /etc/passwd
```
```
cp /etc/shadow-backup /etc/shadow
```
and
```
cp /etc/group-backup /etc/group
```

---

### Post by csh on 2009-05-27
Thank you! However, I had just reinstalled my ubuntu. Thanks for everybody.

---

