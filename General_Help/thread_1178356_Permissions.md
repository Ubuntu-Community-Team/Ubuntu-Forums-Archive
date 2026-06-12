---
title: "Permissions"
date: 2009-06-04
forum: General Help
---

### Post by Freddy on 2009-06-04
Hi all.

How can I give a second user 'sudo' privileges on this account. I have no access to the orginal account, cause I have messed things up severly and nedd this second account to use my computer.

/Thanks.

---

### Post by Chronon on 2009-06-04
Are you saying you have no administrative privileges with the current account?

---

### Post by sjuranic on 2009-06-04
The way to add new sudo privileges is via the "visudo" utility (man visudo).  The only catch here is that you need root to use visudo.  So if you've lost your root password, this isn't going to help you.

---

### Post by Polaris96 on 2009-06-04
The question is TOTALLY, "do you have any administrative priviledges now?"  If the answer is "No,"  I believe you are in trouble.

If you can get admin priviledges, there's a lot you can do.  The easiest thing is to create the new user within you window manager.  I use KDE but if you're gnome it shouldn't be that different.  Select "user account" from the system settings submenu and find the listing for "add a new user".  when you do, there should be a tab for "groups".  Select it and make sure the "admin" group is checked.  There may, alternatively, be a prompt like,"should the user be allowed to administer the computer?"  Obviously, click yes, there.

If that's not working I can give you some BASH code that you can use from a terminal session, but I don't want to type it all out unless you can sudo, now.  If you can't use su or sudo, I don't know of anything that can be done.

Also, regarding visudo, I wouldn't do it.  usually the way to add sudoers is by adding the 'admin' group to a user's groups.  sudoers is better for creating specialized sets of admin priviledges than it is for adding administrators.  It's also real easy to screw up big.  stay away from sudoers unless you REALLY want to take a chance.

---

### Post by Paul41 on 2009-06-04
See if you can fix it with this.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Celauran on 2009-06-04
> **Freddy said:**
> Hi all.

How can I give a second user 'sudo' privileges on this account. I have no access to the orginal account, cause I have messed things up severly and nedd this second account to use my computer.

/Thanks.

Can you not log in to the original account at all, or can you simply not use sudo from that account? If it's the former, the link above looks good. If it's the latter, you could try booting from a LiveCD, mounting the HDD, and editing /etc/group manually.

---

### Post by DeMus on 2009-06-04
> **Freddy said:**
> Hi all.

How can I give a second user 'sudo' privileges on this account. I have no access to the orginal account, cause I have messed things up severly and nedd this second account to use my computer.

/Thanks.

Yesterday around this time of day there was another user who had the same problems. It seems to be possible to boot without passwords and then set a new password for your account. Just start looking here for threads which are about 24 hours old.

I do realize it is a shot in the dark so I helped you looking for the thread. I found two of them. Just have a look here:
[http://ubuntuforums.org/showthread.php?t=1175930&highlight=user+root+account]("http://ubuntuforums.org/showthread.php?t=1175930&highlight=user+root+account")

and here
[http://ubuntuforums.org/showthread.php?t=1177638&highlight=user+root+account]("http://ubuntuforums.org/showthread.php?t=1177638&highlight=user+root+account")

Success

---

### Post by Freddy on 2009-06-04
Thanks all. 

'adduser username admin' from 'rescue mode' did the trick, finally I could locate and fix the problem with my previous user account.

/Freddy.

---

