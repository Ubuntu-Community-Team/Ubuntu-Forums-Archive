---
title: "Hide lost+found in samba share"
date: 2011-07-14
forum: Desktop Environments
---

### Post by ozz_man on 2011-07-14
I made an entire large drive into a samba share, but I don't really want users to see the lost+found directory, how can I hide it (want to avoid user curiosity)?

Does "veto files" and "hide files" work using the "simple" file sharing (through Nautilus)?  Or does that only work when you configure through smb.conf file?

---

### Post by Juxe on 2012-08-25
Found the answer here: [http://ubuntuforums.org/showthread.php?t=810813](http://ubuntuforums.org/showthread.php?t=810813)
Essentially this: ```
   hide files = /lost+found/

or

   hide unreadable = yes
``` in a share definition of /etc/samba/smb.conf

---

### Post by overdrank on 2012-08-25
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

