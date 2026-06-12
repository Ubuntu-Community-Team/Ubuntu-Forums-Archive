---
title: "Poof, GNOME went bye bye"
date: 2007-06-07
forum: Desktop Environments
---

### Post by theyain on 2007-06-07
Earlier today I had restarted my computer to let it cool down for a while.  Then I restarted it.  And low and behold (after I log in) GNOME won't open and the only way to really log in is to use the terminal.


Things to know that might be helpful.

I have a broadband connection, I am on a very old computer (try the year 2000 if not earlier), and the last thing I had uninstalled was the Evolution email client (I don't use them).  Which, oddly enough, had uninstalled Nautilus, so I reinstalled that (Nautilus).  Now I can't seem to do anything.  And Reinstalling Ubuntu would be a last resort do to how much artwork and mission critical information I have on there.
Also, I am using Feisty Fawn


Please, I need help trying to either reinstall GNOME or reenable it.

---

### Post by SoggyCornflake on 2007-06-07
> **theyain said:**
> 
Please, I need help trying to either reinstall GNOME or reenable it.

My Guess is that the login program, GDM, was nuked.  Try this from the terminal after you login:```
 sudo dpkg-reconfigure gdm 
```

---

### Post by theyain on 2007-06-07
That didn't work, but thanks.

---

### Post by floke on 2007-06-07
Do you get any error messages at all?
Can you log in to failsafe gnome?
What I'm thinking is that your configuration settings could have gotten borked - has happened to me before - in which case you need to reset them by deleting the files. You might have to do this via a live CD if sudo rm [name] doesn't work for you in the terminal - but in your home dir. there are the (hidden) gnome config files - they are.

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

Either delete these or - safer - rename them. When you restart gnome it will create new versions of the files - you will lose all your menu/panel configurations - but they're no good to you anyway if you can't log in, right?

Anyhow, this has worked for me in the past.

Hope it helps.

---

### Post by theyain on 2007-06-07
> **Steve.K said:**
> Do you get any error messages at all?
Can you log in to failsafe gnome?
What I'm thinking is that your configuration settings could have gotten borked - has happened to me before - in which case you need to reset them by deleting the files. You might have to do this via a live CD if sudo rm [name] doesn't work for you in the terminal - but in your home dir. there are the (hidden) gnome config files - they are.

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

Either delete these or - safer - rename them. When you restart gnome it will create new versions of the files - you will lose all your menu/panel configurations - but they're no good to you anyway if you can't log in, right?

Anyhow, this has worked for me in the past.

Hope it helps.

I do not *recall*, that is to say I do not know, seeing any errors.  But I do recall seeing something about the HDD (when rebooting before all of this started to happen, right after POST) being mounted over 24 times in the past and needing to be checked.  So it checked it, what ever that means.

And I know what files you speak of (although I do not know the line to delete files) for I saw them today when I tried out the Find command.

---

### Post by diatribe on 2007-06-08
ok so does it bring you to the graphical login where you type in your username and password, or do a command prompt asking you to login?

---

### Post by theyain on 2007-06-08
It actually brings me to the graphical login.  I still have all the little sessions (all but the terminal session are useless) and everything.

---

### Post by bapoumba on 2007-06-08
Before login into GDM, hit <CTRL><ALT><F2>, this will get you to a text-mode session. Login, and run```
df -H
```
See if any of your partition is full.
```
sudo aptitude clean
```
wille make some room on the root (/) partition. If your /home is full, then make some room there.

---

### Post by theyain on 2007-06-08
Nothings full on my HDD.  I have plenty of room left in all the partitions and such.

---

### Post by moron on 2007-06-08
What do you mean by "useless"?  What exactly happens when you attempt to choose a normal Gnome login?  

If you are getting the graphical login it sounds like X is running OK so whatever is going on is specifically with Gnome.  Have you taken a look at the various error logs to see if the problem is noted there?

See if you have a ".xsession-errors" in your home directory and if so, look at what is in it.  Also check in /var/log/ to see if anything in there has useful details (I'm mainly a KDE user so am not sure where Gnome normally writes its errors to, probably gdm.log, Xorg.0.log or messages).

Cheers

---

### Post by theyain on 2007-06-08
As in I get an error saying GNOME can't be found.  And I have no idea on how to see any of those files from the terminal.  I am not that great at using it.

---

### Post by atlfalcons866 on 2007-06-08
try 
sudo apt-get install ubuntu-desktop

---

### Post by theyain on 2007-06-09
doing so right now.  Lets hope that this works!  :D

---

### Post by theyain on 2007-06-09
Thank you!  That worked out perfectly!  :D  I told you that Gnome went bye bye!  :P


RESOLVED!

---

