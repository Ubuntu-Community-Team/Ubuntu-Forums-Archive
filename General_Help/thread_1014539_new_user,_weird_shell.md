---
title: "new user, weird shell"
date: 2008-12-17
forum: General Help
---

### Post by Shwick2 on 2008-12-17
I created a new user, l4d1, then logged into it with "su l4d1".  What is with the new shell?  It's just a question mark "?", no command completion or command history.

The l4d1 user doesn't have a password and can only be logged into with "su l4d1".

---

### Post by cariboo on 2008-12-17
That really makes no sense, as well as not being very secure. What kind of users did you set up? If you need to be root to do anything you should use:

```
sudo -i
``` 

This will drop you to a root prompt until you log out.

Jim

---

### Post by Shwick2 on 2008-12-17
I was reading a left 4 dead server setup guide.  It said to make l4d1 by calling "useradd l4d1", then login it via "su l4d1".

Isn't this secure because l4d1 can only be logged into from root?  But it doesn't have the same priveleges as root.  Therefore no one can login to l4d1 from openssh, and if someone causes a bufferoverflow in the game server they only have l4d1 priveleges, not root priveleges.

[http://left4deadforums.com/1187-left-4-dead-linux-server-guide.html](http://left4deadforums.com/1187-left-4-dead-linux-server-guide.html)

---

### Post by kanikilu on 2008-12-17
As your regular account, can you use *finger l4d1* to see what shell it's using?

If it's set to something other than bash, maybe try using *chsh* to change your shell back (the path to bash is /bin/bash). You can also change a user's shell with *users-admin*.

---

### Post by iponeverything on 2008-12-18
This will show you the shell too:

```
grep l4d1 /etc/passwd
```

---

### Post by jerome1232 on 2008-12-18
> **Shwick2 said:**
> I was reading a left 4 dead server setup guide.  It said to make l4d1 by calling "useradd l4d1", then login it via "su l4d1".

Isn't this secure because l4d1 can only be logged into from root?  But it doesn't have the same priveleges as root.  Therefore no one can login to l4d1 from openssh, and if someone causes a bufferoverflow in the game server they only have l4d1 priveleges, not root priveleges.

[http://left4deadforums.com/1187-left-4-dead-linux-server-guide.html](http://left4deadforums.com/1187-left-4-dead-linux-server-guide.html)

I'm pretty sure ANY user can use su (**s**witch **u**ser) to login to a different user, so having l4d1 with no password is a bad idea, any user could log into that user and mess with the files it has rw acces to. Probably should set a password on that account using the passwd command as well.

---

