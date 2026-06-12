---
title: "Nautilus file permissions?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by hizaguchi on 2006-03-06
I'm having a little problem with Nautilus.  I'm using sshfs to remotely mount my university file space on my laptop, for managing files and working on my website.  Most applications work perfectly with this, but Nautilus doesn't seem to understand that I have write permission for the remote files.  I can access things fine, but I can't delete or save anything though Nautilus.  Is there a fix for this?

---

### Post by hizaguchi on 2006-03-07
Shameless bump from 4 pages down:

I've been reading everything I can on the subject, and it looks like the problem might be with Gnome-VFS.  Ring any bells for anybody?

---

### Post by joehill on 2006-03-18
Just to say that I have the same problem.  For the most part sshfs works well, like a transparent part of the filesystem (I was glad to find this after spending forever trying to get nfs to work).  But some things don't work, because some parts of the system are looking at the UID on the server rather than the fact that I'm mounting it with that user's credentials.

Nautilus tells me I don't own the files, so I can't rename them or change their permissions (although for some reason it lets me move them around). When I try to move files with the command line, I get the message: 

```

mv: failed to preserve ownership for `myremotedirectory': Permission denied
```

...but it still usually moves the file (and sometimes doesn't).

I'd be glad for any input.

---

