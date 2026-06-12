---
title: "hide all but home dir"
date: 2005-08-04
forum: Desktop Environments
---

### Post by gtstdiy on 2005-08-04
Hi there people,

is there a way that I can make it so that a particular user can see ONLY their home directory, and nothing else on the drive?ie-hide all folders but there /home/<user>

I can set various permissions and stuff, but folders are always stil visible - I would like them to all be hidden rather than inaccessable.

Cheers,


Lincoln.

---

### Post by cwaldbieser on 2005-08-04
Well, the closest I can figure out at the moment would be to remove the read permission on the /home directory for all users (except maybe root).  Then no one can list the contents of /home at all.  Users can still cd to directories they know about and have permission to enter.  They just can't see any home directoroes.  Of course, you can always change to your own home with "cd".

---

### Post by Hikaru79 on 2005-08-04
What I would do is set that user's ~/.bash_profile to chroot them into their own home dir.

---

### Post by gtstdiy on 2005-08-05
so there is no way to make /etc, /dev, /usr etc etc all invisible to a user?

---

### Post by Hikaru79 on 2005-08-05
[QUOTE=gtstdiy]so there is no way to make /etc, /dev, /usr etc etc all invisible to a user?[/QUOTE]
... yes there is, I just said it. Make that particular user's .bash_profile chroot them into their own home dir. Problem solved! (Unless they know the sudo password)

---

