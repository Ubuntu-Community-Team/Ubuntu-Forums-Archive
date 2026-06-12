---
title: "Can't log in to Ubuntu - write error message. Help?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Rory on 2006-08-18
I am getting the following error message and can no longer sign in to Ubuntu.  

> "GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator."

This may be the result of a full HD, but my hard drive shouldn't be anywhere close to full.  I am currently writing this via Knoppix 3.7, as it's the only way I can access the internet.  I have tried to access terminal in Ubuntu ("Failsafe terminal" from GDM) but I get the same error message.  

I have tried to delete some files via Knoppix to free up space and rule this out, but Knoppix won't let me remove the files from the drive and I don't know enough about Knoppix to know how to bypass it.  

I can't just re-install as I have some valuable work files I'd like to retrieve.

Any simple to follow advice anyone can provide would be greatly appreciated.  

Rory

---

### Post by jimbren on 2006-08-18
I've run into this same issue in the past once or twice.  It is usually the result of running some X app as root, and can be easily remidied.  

Reboot into your Ubuntu installation and either drop to a console or failsafe.  At a prompt, do the following:
```
ls -l |less
```

from the output, you'll be able to see that some files are now owned by root.  

Now do this:
```
sudo chown yourusername:yourusername *.*
```

when you return to the prompt, repeat the file listing
```
ls -l
```

and you'll see that you're now the owner of all the files.

then logout, and you should be able to log back into your X session.

---

### Post by Rory on 2006-08-18
Good tip!  Will keep it handy.  Thanks!

---

