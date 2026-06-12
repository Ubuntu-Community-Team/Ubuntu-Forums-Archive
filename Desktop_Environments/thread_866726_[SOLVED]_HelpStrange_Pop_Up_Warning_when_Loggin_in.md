---
title: "[SOLVED] Help:Strange Pop Up Warning when Loggin in"
date: 2008-07-22
forum: Desktop Environments
---

### Post by pmlxuser on 2008-07-22
I recently did a system reinstall Ubuntu 8.04. everything went on fine the system performs nice only one problem: when i log in before my desktop (gnome) loads a strange pop up message papers it says.

> 
User's $HOME/.dmrc file is being ignored
This prevents the default session and language from being saved.
File should be owned by user and have 644 permission. User's $HOME
directory must be owned by user and not writable by other users


when i click [OK] everything goes on as normal. but the message is really annoying any help.

---

### Post by eentonig on 2008-07-22
Read the message.

- check you $HOME for a (hidden) file .dmrc and verify if the permissions are set as mentioned in the error (644).
- Check if your $HOME (/home/<your_username>) folder is indeed owned by you and not writable by others.

---

### Post by sdennie on 2008-07-22
Along with what eentonig said, you can probably fix the problem with:

```

cd
sudo chmod 0644 .dmrc
sudo chown **your_username**:**your_username** .dmrc

```

Though, it's odd that you would get this message in the first place (unless you saved your home directory over the re-install and have a different user ID after the re-install).  I would try doing the following:

```

cd
find . ! -user **your_username**

```

If you get back a lot of files, or "Permission denied", try running:

```

sudo chown -R **your_username**:**your_username** /home/**your_username**

```

---

### Post by pmlxuser on 2008-07-22
> **vor said:**
> Along with what eentonig said, you can probably fix the problem with:

Though, it's odd that you would get this message in the first place (unless you saved your home directory over the re-install and have a different user ID after the re-install).  I would try doing the following:
[\QUOTE]
Yeah i forgot to mention that I am the sole user of the laptop and have a separate partition for /home. During the re-install i just formated the / partition, I used the same username during re-install.

[QUOTE]
```

cd
find . ! -user **your_username**

```

If you get back a lot of files, or "Permission denied", try running:

```

sudo chown -R **your_username**:**your_username** /home/**your_username**

```

Results 
```

pmlxuser@pmlxuser-laptop:~$ cd 
pmlxuser@pmlxuser-laptop:~$ find . ! -user pmlxuser
pmlxuser@pmlxuser-laptop:~$ sudo chown -R pmlxuser:pmlxuser /home/pmlxuser
[sudo] password for pmlxuser: 
chown: cannot access `/home/pmlxuser/.gvfs': Permission denied
pmlxuser@pmlxuser-laptop:~$ 


```

---

### Post by sdennie on 2008-07-22
> **pmlxuser said:**
> 
```

pmlxuser@pmlxuser-laptop:~$ cd 
pmlxuser@pmlxuser-laptop:~$ find . ! -user pmlxuser
pmlxuser@pmlxuser-laptop:~$ sudo chown -R pmlxuser:pmlxuser /home/pmlxuser
[sudo] password for pmlxuser: 
chown: cannot access `/home/pmlxuser/.gvfs': Permission denied
pmlxuser@pmlxuser-laptop:~$ 

```

The .gvfs error shouldn't be fatal.  .gvfs is its own mount point and I just tried to delete it in a clean VM of Ubuntu 8.04 and it gave me the same error.  This is probably more of a feature than a bug because ~/.gvfs will often contain network shared folders and so an errant chown from there could be unwanted.

Regardless, is your .dmrc problem fixed?

---

### Post by pmlxuser on 2008-07-22
> **vor said:**
> .

Regardless, is your .dmrc problem fixed?

so Far its not solved I logged out and when i logged in it still come
isn't there a command i can use to recreate this file?

---

### Post by sdennie on 2008-07-22
It looks like that file is autocreated if it doesn't exist.  Try:

```

mv .dmrc .dmrc.bak

```

Logout and then log back in.

---

### Post by pmlxuser on 2008-07-22
did not work..

---

### Post by sdennie on 2008-07-22
Ok, I was able to reproduce this doing a "sudo chmod 777 /home/username".  To fix it, try:

```

sudo chmod 0755 /home/**your_username**

```

Those are the default permissions for a home directory and should fix the problem.

---

### Post by pmlxuser on 2008-07-22
Thanks that worked ;)
now how do i mark this as solved?

---

### Post by hoax.it on 2008-07-22
but 777 is safe ?
i think not at all:mad:

---

### Post by sdennie on 2008-07-22
> **hoax.it said:**
> but 777 is safe ?
i think not at all:mad:

No, 777 is not safe for the permissions on a home directory.  The error message was for exactly that reason.  In order to fix the problem it was useful to reproduce it and by changing the permissions on a home directory in a VM to 777 I was able to so.  By then changing the permissions to 755, I was able to fix it.  :)

---

