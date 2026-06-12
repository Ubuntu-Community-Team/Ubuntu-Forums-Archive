---
title: "adding users"
date: 2005-04-27
forum: Desktop Environments
---

### Post by iamkmaniam on 2005-04-27
I was wondering if anyboby else noticed the switch from the "useradd" command to the "adduser" command. I have used many distros and this is the first time I ever used the "adduser" command. I was wondering if this is the start of a new standard. Like when distros started adding the cdrom drives to /media instead of /mnt. I also noticed the GUI for adding users did not function properly it failed to create a /home directory for the new user. The "useradd" command gave me the same results. This is  not really a problem it just threw me off a bit.

---

### Post by nad on 2005-04-28
This is certainly a problem! Is it not defaulting to a valid completed /home entry?

Are complete entries being made to /etc/passwd? At a terminal screen?

---

### Post by iamkmaniam on 2005-04-28
Hi Dan
Yes entries are being made to /etc/passwd for the user, but no "home" dir is being created. in /home of  / I should have said that "if they were changing the commands it wasn't a problem" how ever if useradd is supposed to function yes then it is a serious bug. Should I file a bug report with Ubuntu?

---

### Post by kris kincaid on 2005-04-28
I have been using 

System > Administration > Users and Groups , then Add User. 

Works pretty nice.  :)

---

### Post by nad on 2005-04-28
This is odd. How is your disk space? Although root should be allowed to fill the disk, the /home/~ directory has permissions of the user...

Perhaps someone more knowledgeable will chime in.

---

### Post by iamkmaniam on 2005-04-28
Yeah I thought it was odd too. To answer your question I have roughly 35 gigs left on the drive, so drive space is not a problem. I'll let this post go a little longer then report this as a bug to the Ubuntu developers.

---

### Post by jean on 2005-05-06
have any of u guyz faced this while adding a new user? 
#useradd -d /home/smith  smith
and when u go to the /home directory after this,you dont see the new directory 'smith' that was supposed to be created as specified....

---

### Post by shakin on 2005-05-06
[QUOTE=jean]have any of u guyz faced this while adding a new user? 
#useradd -d /home/smith  smith
and when u go to the /home directory after this,you dont see the new directory 'smith' that was supposed to be created as specified....[/QUOTE]

I just run 'sudo adduser smith' and it creates the user with the home directory. No problem at all.

---

### Post by iamkmaniam on 2005-05-07
Yes this is exactly what I was talking about. the "adduser" command works however the "useradd" command will seem to work, that is Ubuntu accepts the command, but does not create a home directory for the newly added user.

---

### Post by Adamal on 2005-11-13
This is a little old but I thought I'd help.

use the -m parameter.  It will cause useradd to create the home directory.

---

