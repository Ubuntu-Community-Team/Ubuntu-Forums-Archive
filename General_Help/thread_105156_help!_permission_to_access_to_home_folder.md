---
title: "help! permission to access to home folder?"
date: 2005-12-17
forum: General Help
---

### Post by justinesalo on 2005-12-17
any help would be awesome.  here's what happened:

i was moving files around and messing with the permissions to cut and delete.  i opened a playlist for totem and the computer stopped responding, so i did ctrl+alt+backspace.  after entering my logon info, i got an error saying something like:

"your $home./dmrc is being ignored, permissions should be set to 644."

then for some reason i couldn't open totem again (clicking it did nothing, though this might have been a one time thing), so i messed with my home folder permissions until it said 644 (all could read, user could read and write but execute was unchecked for all).  then ubuntu freaked out, i got errors doing anything (because the home folder couldn't be accessed i assume) and somehow my entire screen became the terminal.  i typed in random stuff like "set execute true" but i don't think that did anything, so i restarted. at restart, after entering my login i now get an error saying:

"your last sesion only lasted less than 10 seconds...installation problem..." with details saying:
"libgnomevfs-WARNING: unable to create ~/.gnome2 directory: permission denied 
could not create per-user gnome configuration directory `home/vreonica/.gnome2/` permission denied"

i can't run in any of the sessions on the login screen except failsafe xterm, which has an error script on the top reading:
"bash:home/veronica/.bashrc: permission denied"

any ideas what i could type in that terminal to give me access to my home folder again or just let me logon?

---

### Post by tm8992 on 2005-12-17
I'm no Linux expert, so don't be surprised if this doesn't work :p

Try:
```

chmod -c 0777 home

```

That should change the permissions of home.  Make sure you are in the very top of the filesystem, though (you can't go "up" any more), type ```
cd ..
``` a few times if you'd like :p

Tim

---

### Post by aysiu on 2005-12-17
You could try this: ```
sudo chown -R veronica:veronica /home/veronica
```

---

### Post by justinesalo on 2005-12-17
thanks for the idea, but it only spits out:
"chmod: changing permissions of 'home': Operation not permitted"

any other suggestions?  please?

---

### Post by aysiu on 2005-12-17
Are there any other users on your computer?

P.S. Are you able to log in on the black screen with white text (not graphically... just at all)?

**Edit**: Maybe this might help?
[http://ubuntuforums.org/showthread.php?t=91455](http://ubuntuforums.org/showthread.php?t=91455)

---

### Post by prizrak on 2005-12-17
[QUOTE=justinesalo]thanks for the idea, but it only spits out:
"chmod: changing permissions of 'home': Operation not permitted"

any other suggestions?  please?[/QUOTE]
Make sure you use 'sudo' if you are it cannot possibly deny you privileges. If that fails try doing sudo su to put you in full root mode and then run what aysiu said without 'sudo' in the front.

---

### Post by justinesalo on 2005-12-17
thanks for all your help.  here's the fix for future google goodness:

there weren't any other users, which gave me the idea. 
first i did both:
sudo chown -R veronica:veronica /home/veronica
and (from the other thread):
sudo chown veronica .dmrc
sudo chmod 644 .dmrc
all they did was bring up a new prompt line, didn't indicate anything had been done.  i powered off and on again, but still get the same error for any login but the terminal:

/etc/gdm/presession/default: registering your sesssion with wtmp and utmp
/etc/gdm/presession/default: running: /usr/bin/XII/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "veronica"
/etc/gdm/XZsession: Beginning session setup...

(gnome-session: 7798): libgnomevfs-WARNING**: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/veronica/.gnome2/': Permission denied


here's what worked--login as root (su root) in the failsafe terminal and add user using:
adduser <user>
(go through the process--it's self explanatory)
restart and login as the new user
open a terminal (applications>accessories>terminal)

su root
<enter yr password>
nautilus
locate messed up home folder and fix permissions so that everything is checked except the "Write" option for "Group" and "Others" (=755) 

this fix for this message after login: 
your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File sould [sic] be owned by user and have 644 permissions.

can be found here:
[http://forum.deviantart.com/os/unix/528986/](http://forum.deviantart.com/os/unix/528986/)
for me, the answer was the same as for hir--setting the home directory permissions to 755 (unchecking the "Write" option for "Group" and "Others"). 

>>i think the error message should have read "have 755 permissions"...if i'm right, someone should correct that, because setting your home folder to 644 does bad, scary things.

---

