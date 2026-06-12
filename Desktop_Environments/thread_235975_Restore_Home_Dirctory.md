---
title: "Restore Home Dirctory"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Socratez on 2006-08-14
I am getting an error when I log into my Gnome session. It wants to "Delete" or "Don't Delete" my applets for Trash, Battery and Sound. I am not sure what had happened but I did perform a CTRL+ALT+BACKSPACE to restart the Xserver just before this happened. I assume I corrputed something. So in an attempt to fix it I deleted all the .blah (.bashrc .bash_logout, etc etc)files from the user home directory. I just ended up messing things up even more. Is it possible to restore thes files and get things back to orginal first time login? I spent 1.5 hours updating and configuring my Ubuntu today and would rather not reinstall and begin again.

Thanks in advance

Soc

---

### Post by andb on 2006-08-14
Easy way if you can still get into the graphic interface would be 
System > Administration > Users and Groups

and add a new user. Log in with that. should work. If you really care about your old uid (all users have a unique id, the first user acct is 1000) then you could mv the new home to the old's place.

Lots of ways to fix this, but this one is the easiest I can think of...

oh, and now you see why backing up is a good practice ;)

---

### Post by Socratez on 2006-08-14
I did that already and it doesn't solve a thing. I thought it would work too but the new user gets the exact same error message. I even retried that with a 3rd user but same results. I forgot to mention that in the original post. Any other ideas other then this one?

Soc

---

### Post by andb on 2006-08-14
well, all the .bash* files only set up terminal anyway... If you remove the Trash, Battery and Sound applets, log out, then log in, is everything ok? Asuming yes, if you add them back to the pannels, does the problem persist?

---

### Post by ardchoille on 2006-08-14
You could always restore from a backup. You have been making backups haven't you?

Easy way to set up backups:

Make a backup directory
1. sudo mkdir /home/backups
2. sudo chown user:user /home/backups
Where "user" is your username

Make the backups and store them in the backup directory
1. cd /home
2. tar cjf /home/backups/$(date +%Y%m%d)-backups.tar.bz2 user

Again, where "user" is your username.

This will make backup files in /home/backups with the date in the filename, like this: 20060814-backups.tar.bz2

I use this in a cronjob for nightly backups. That way, if anything goes wrong, I can just restore from a backup.

---

### Post by andb on 2006-08-15
Ardchoille, it seems that he is refering to restoring the config files for Gnome, and he is assuming they are in the home directory. The real problem, if i uderstand correctly is his 'delete/dont delete" message (I'd like more detail on that one too).

---

### Post by sdebo on 2006-08-15
Sorry for sounding naive but I am still a noob.

What do your backup instructions back up?  User settings? Program settings? The actual software applications?  Is it similar to restore points on XP?

How does one restore from old backups please?

Thanks in advance?

---

### Post by Lunar_Lamp on 2006-08-15
That will backup everything in your home folders.  All your users and their settings, but not programs installed (unless they were installed into home for some reason).

---

### Post by sdebo on 2006-08-15
Thanks.  Will overwriting the home directory with a backup sort of restore the previous settings or is it likely that some application will expect to find some overwritten setting and crash?

Restoring settings is a matter of unpacking the backup over the home directory, right?

---

### Post by andb on 2006-08-15
sdebo, for the most part settings are stored in two places: /etc and /home/USERNAME

/etc is system specific. You'll find startup scripts, samba config, firewall config, all the stuff that any user on the machine would need. In home you find program specific stuff. Desktop options, program behavior, stuff that every user wants to be able to customize. And when you upgrade, just move over your home dir and you should be pretty happy to find its what you had before.

depending on how you "write over" your directory, it might wipe out anythign with the archived version, might only replace if the write date in newer, depends what you've done. Advantage over windows, you can do it exactly as YOU want. Disadvantage, you first have to figure out what YOU want, then actually make it. Takes a bit longer but in the end works just right. Lots of good sources for info on what config files are where can be found on the linux documentation project.

---

### Post by sdebo on 2006-08-15
You have been of great help. Thank you

---

