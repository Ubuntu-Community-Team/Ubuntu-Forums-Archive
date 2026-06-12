---
title: "User creation problem"
date: 2005-12-20
forum: Desktop Environments
---

### Post by stalefries on 2005-12-20
What command do I use to open the Users/Groups settings page? If I can't do that, is it possible to create new users from gnome-terminal? Can I make them of type "Administrator" like it is done in the graphical client? 

My problem is, my gnome-panel is broken, so I want to create a new account for myself, because I have not been able to fix it. Thus, I cannot open the the Users/Groups settings editor.

---

### Post by Sutekh on 2005-12-20
```

sudo adduser <username>

```
Will add a new user.
```

sudo adduser <username> **adm**

```
Will add that user to the adm group - which has admin privileges.

---

### Post by stalefries on 2005-12-20
Thanks.

---

### Post by stalefries on 2005-12-20
How would I remove a user?

---

### Post by Sutekh on 2005-12-20
deluser, i think?  I'm not 100% sure form the command line.  If your new user can get back into gnome, then I'd use the GUI, to remove the old user.

Some google stuff

```

deluser - Debian specific

A different front end to the userdel. It can remove the home directory, 
or all files on the system owned by the user based on the options specified.
Command 	Action
deluser 	Does not remove the home directory, mail spool, or any files owned by the user
deluser -remove-home user 	Removes the home directory and mail spool
deluser -remove-all-files user 	Removes all files on the system owned by the user

```

Type
```
man deluser
``` for the ubuntu man page, just to check.

---

### Post by stalefries on 2005-12-20
The first time I tried, it said I was not allowed to use sudo. I added myself to group "sudo", and from then on it failed and exited with a "1 status".

Edit: I just added myself to group root, and it hasn't changed anything. By the way, I plan on using the created account to remove and then remake account #1, as that account has my prefered username.

---

### Post by Sutekh on 2005-12-20
When you create the new user, you must be logged in as the old one (which has sudo privileges), then to add the new user to the **adm** group (not sudo), you still need to use the old user's login (and sudo privileges).  Did you do it this way?

---

### Post by stalefries on 2005-12-21
[QUOTE=Sutekh]When you create the new user, you must be logged in as the old one (which has sudo privileges), then to add the new user to the **adm** group (not sudo), you still need to use the old user's login (and sudo privileges).  Did you do it this way?[/QUOTE]
Um, I think so. I might have done it as root. Root is enabled because Automatix enables it.

---

### Post by stalefries on 2005-12-21
I finally got it all fixed! In the end, I removed everything from user 1's home directory, then copied all off user 2's stuff into it. All fixed, and I managed to clean out about 2 gigs of stuff in the process. Don't worry, though, I backed up all my stuff I wanted.

By the way, the command for the graphical client is "users-admin".

---

### Post by tipp98 on 2007-02-09
I just struggled with a similar problem. I was trying to rename the username, password, and home directory for the administrator account. When I tried to log back in I could not, not with the new username/password or the old anyway. After racking my brain I was able to log into tty1 as root.  "adduser <username> adm" did not work for me. I opened up the /etc/group file and found admin was the group I was looking for. Here is the code I finally found to work.
```
ctrl + alt + F1
```
root login
```
useradd -m -g admin fred
passwd fred
```
I'm not sure if creating a home directory (-m) is necessary.  After this I was able to log in and remake my administrator account, although I had to go back to my root login to delete it first, as it was not on the list but told me it already existed.

---

