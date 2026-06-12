---
title: "Trouble logging in to recent ubuntu 9.04 installation"
date: 2009-05-09
forum: General Help
---

### Post by Colci on 2009-05-09
I messed around with the file permissions (don't ask why) and now I cannot log in.  Before I wipe it and start again I wonder if anyone can help.

I can log in but I do not log into the orginal installation (called gig-ubuntu) but colci@localhost.

I was getting originally getting some error messages which I have fixed by changing the permissions, namely:-
users $home /,dmrc file is being ignored etc. and 
must be setuid root

Now whenver I try and do anything I get a message
"not allowed to access system configuration"

I cannot access my network and hence the internet

Is there a way to reset ubuntu and put it back to how it was beofe I started messing around?
Thanks

---

### Post by cariboo on 2009-05-09
Start in recovery mode, and set the proper permiisions for your home directory. THey should be set to at minimum 755, I have my home directory permissions set to 750

```
chmod -R 755 /home/colci[/CODE

You will get an error that the permissions for ~/.gvfs can't be changed, just ignore the error.

Then set the proper permissinons for ~/.dmrc

[CODE]chmod 600 /home/colci/.dmrc
```

---

