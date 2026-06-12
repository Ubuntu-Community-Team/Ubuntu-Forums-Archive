---
title: "How do I change my UID/GID?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Poeffie on 2006-09-17
[CENTER][SOLUTION HERE \/ \/ ]("http://ubuntuforums.org/showthread.php?p=1514766#post1514766")[/CENTER]

I've got two/three pc's on diffrent locations wich I want to syncronize a bit. I've been told I have to change the UID's and GID for the three accounts wich I'll need to use (mostly for documents). Searching around mostly on this forum I havent found any guide wich explains how I should do this.

So:
*how do I change 3 userid's for all my documents on 3 pc's (already under the right user, but not the same ID on each pc) without dataloss etc..
*same for the gid's

also:
*Is it possible to transfer settings (x-configuration, browsers & other software) and maybe syncronize them?

I'm using the latest version of Ubuntu (Gnome & DD 6.06) and have a good knowledge about administrator functions & terminal commands.

Thnx,
Raven

---

### Post by mlind on 2006-09-17
I think you shouldn't change the UID/base GID of your useraccount(s), but sync files in a way that they get default permissions (and ownership) of the user who is doing the sync.

If you really want to change UID/GID, I guess you need to delete user and create new one using adduser --uid xxx username and addgroup --gid xxx groupname, where x's are numbers. deleting user using deluser doesn't remove user's files.

---

### Post by sontek on 2006-09-17
usermod -u [UID] [USERNAME]

---

### Post by Poeffie on 2006-09-18
> **sontek said:**
> usermod -u [UID] [USERNAME]

Yes, i've already tried that. The only problem is that my X cannot startup anything anymore and I had to go to my main terminal to reverse it to 1000

My question was: is there a way to do this safe, so everything works again?
I've heard things as changing /etc/passwd but I dont know what exactly. Also shouldnt I work in full terminal mode (no X server)?

---

### Post by Poeffie on 2006-09-18
I've solved my problem:
(Here I use nano, but it is the same for every terminal editor)

1. Open your terminal
(! best is safe mode terminal (root preferred) or a root terminal in Ctrl+Alt+F1)
> nano /etc/passwd
2. Change the usernames's UID (1000 and 1001 originally)
one time per user
[INDENT](*)Keep it >999 for users[/INDENT]
3. Add a user with UID 1000 in the same way the other users were described:
```
<USERNAME>:x:1000:<***>:<FULL NAME>,,,:/home/<USERNAME>:/bin/bash
```
[INDENT](**)  You can use any username you like, you just need a user with UID 1000 or it might give some problems[/INDENT]
[INDENT](***) Same as the number used with other users, this may change (I've seen 1000 & 100) I think it stands for a certain group nr.[/INDENT]
> nano /etc/group
4. Change the GID's the same way you did in /etc/passwd
5. Add a usergroup with GID 1000:
```
<USERNAME>:x:1000
```
6. Modify for each user the account with:
> usermod -u <UID> <USERNAME>
7. Own the files to the right user:
> chown -R <USERNAME>:<USERNAME> /home/<USERNAME>
8. Check if every /home directory has the right owners:
> ls -alh /home
9. Reboot
> reboot

|) This worked for me, and I hope it will be useful for other people
!)It is possible that steps 2->5 & 6 do the same thing, but I used both just to make sure.

---

