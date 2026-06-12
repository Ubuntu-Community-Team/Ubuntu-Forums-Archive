---
title: "Changed something with KDE control center and now getting DBUS errors, etc."
date: 2010-02-18
forum: Desktop Environments
---

### Post by CharlieNewey on 2010-02-18
Hi,

Recently I've been using Backtrack (which is based on Kubuntu 8.10) as one of my main operating systems, mainly because I had it on a live USB at the time, and I quite like it. Problem is, I changed something in the KDE control center, under the System Administration -> Paths section, to try and get my Desktop folder to work the way it should. Basically here's what I did by mistake:

Change Desktop location to /root/Desktop
This threw up some errors, so I tried:

Change Desktop location /root/
This got things working as before, but here's where I made the mistake...

I think I changed the Desktop location to /... which isn't clever. I tried to undo this, and it copied ALL system files into my /root/Desktop/ folder. I moved the files back to where they should be, but on startup I'm still getting some errors, all to do with DBUS not being able to start.

This is annoying because it was such a stupid mistake!

Can somebody help me?

Thanks in advance.


EDIT: Reinstalled Kubuntu, that fixed things. :)

---

### Post by Zorael on 2010-02-19
See [this post and thread](http://ubuntuforums.org/showthread.php?p=8320656) for some more information about the whole Path section moving files deal.

As for DBUS errors, I guess that could be caused by permissions in your home being set up wrong somehow. Instead of reinstalling, you could also have created a new user, and gradually migrated your old settings to it.

---

