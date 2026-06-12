---
title: "simple bash script containing parentheses"
date: 2009-01-05
forum: General Help
---

### Post by citizenphil on 2009-01-05
I'm trying to write a simple bash script to remove all (non-hidden) files from a user's home directory. I'd like this script to run each time the machine boots (This computer is just for internet access; no one should be permanently saving personal files to it.).

I've had problems just deleting everything in the home folder, as that deletes the Desktop directory, and that's caused problems.

So I wanted to execute these two commands in a script:

```
rm -rf /home/username/!(Desktop)
rm -rf /home/username/Desktop/*
```

These both work if I enter them manually in a terminal, but when I run the script I get this error:

> /usr/local/sbin/rc.local: line 3: syntax error near unexpected token `('
/usr/local/sbin/rc.local: line 3: `rm -rf /home/username/!(Desktop)'

I've tried these alternatives to the first command and none works.

```
rm -rf "/home/username/!(Desktop)"
rm -rf '/home/username/!(Desktop)'
rm -rf /home/username/!\(Desktop\)
```

This prevents the error and allows the second command to run successfully, but in no case does the script remove anything from the home directory except for what's in the Desktop folder.

Sorry for the long-winded post. I've been looking for answers about this for a while and have found nothing.

Any ideas?

---

### Post by heindsight on 2009-01-05
why not just do
```

rm -Rf /home/username/*
mkdir /home/username/Desktop

```

Is there any particular reason for needing to keep hidden files intact? this means that users could permanently save personal files simply by making hidden files or putting files in hidden directories.

What you could do is to completely remove the home directory and recreate it each time. You could just use /etc/skel to recreate by doing:
```
cp -d --preserve=mode /etc/skel /home/username
chown -R username.username /home/username
```
or if you need some specific configuration for that account you could set up the home directory as you want it, make a backup copy of it and then just restore that each time.

---

### Post by citizenphil on 2009-01-07
Thanks for the suggestions. Deleting and then recreating the Desktop folder, for some reason, didn't work as expected. On reboot, what we'd have was a folder on the desktop called 'Desktop'. Strange.

Keeping hidden files was just a way to avoid wiping out all configuration while preventing buildup of junk files from casual users who don't care to clean up after themselves. Not a perfect solution.

In any case, making a backup and restoring it each time (I'm thinking rsync --delete), sounds like a better way to go.  I'd use the /etc/skel method, but there's some custom Firefox configuration I'd like to keep intact.

Cheers.

---

### Post by heindsight on 2009-01-07
> **citizenphil said:**
> Thanks for the suggestions. Deleting and then recreating the Desktop folder, for some reason, didn't work as expected. On reboot, what we'd have was a folder on the desktop called 'Desktop'. Strange.
Very strange - just tried it on my machine: created a new user called test, logged in as the new user, logged out, using my normal account did:
```

sudo rm -Rf /home/test/*
sudo mkdir /home/test/Desktop
sudo chown test.test /home/test/Desktop

```
then logged in as test again - it worked correctly (ie. no folder called Desktop showing up on the desktop).

I know that the first time you log into gnome, the Desktop directory is created automatically (along with the hidden dirs containing gnome's config files), if you delete the Desktop dir but leave other gnome dirs intact then Desktop isn't recreated, instead it uses the home directory as the desktop directory. If I had to guess, I'd say perhaps when you recreated the Desktop dir it had incorrect ownership and that this caused gnome to fall back on using the home dir as desktop dir.

> 
In any case, making a backup and restoring it each time (I'm thinking rsync --delete), sounds like a better way to go.  I'd use the /etc/skel method, but there's some custom Firefox configuration I'd like to keep intact.


In this case i'd say backing up and restoring with rsync --delete looks like the best solution yes. good luck :)

---

