---
title: "KDE 3.5: Autolock on user-witch"
date: 2005-12-25
forum: Desktop Environments
---

### Post by Sokraates on 2005-12-25
I'm using KDE 3.5 and since installing it, whenever I switch between two already loged-in users, the screensaver appears and I'm prompted for the user's password.

Before I could simply switch without screensavers or passwords.

How can I deactivate this behaviour? I don't see any option to turn off the screensaver and if I don't select any, I see a black screen by default. Neither do I see any option to prevent my session from being locked automatically in the first place. :???:

---

### Post by NeoChaosX on 2005-12-25
At the bottom of the Screensaver settings, there should be two checkboxes for "Start automatically" and "Require password to stop". Uncheck both of those.

---

### Post by Sokraates on 2005-12-25
[QUOTE=NeoChaosX]At the bottom of the Screensaver settings, there should be two checkboxes for "Start automatically" and "Require password to stop". Uncheck both of those.[/QUOTE]

They both are unchecked. I tried setting them to "15 Minutes" and "999 Seconds" but it still starts on every switch.

---

### Post by obibok on 2005-12-30
[QUOTE=Sokraates]I'm using KDE 3.5 and since installing it, whenever I switch between two already loged-in users, the screensaver appears and I'm prompted for the user's password.

Before I could simply switch without screensavers or passwords.

How can I deactivate this behaviour? I don't see any option to turn off the screensaver and if I don't select any, I see a black screen by default. Neither do I see any option to prevent my session from being locked automatically in the first place. :???:[/QUOTE]

I can reproduce it here too (also running KDE 3.5).  When switching between X sessions, _sometimes_ they get locked. Usually after a rather long time of not using the other session.  This is certainly a nice security feature but I'd like to know where to control it.

Seems like **/usr/bin/kdesktop_lock --forcelock** gets invoked from **/usr/bin/startkde**

```
# If the session should be locked from the start (locked autologin),
# lock now and do the rest of the KDE startup underneath the locker.
if test -n "$DESKTOP_LOCKED"; then
  unset DESKTOP_LOCKED # Won't need it any more
  kwrapper kdesktop_lock --forcelock &
  # Give it some time for starting up. This is somewhat unclean; some
  # notification would be better.
  sleep 1
fi

```

---

### Post by obibok on 2006-01-13
*bump*

I know *KDE 3.5* is not officially part of *Breezy* but I was hoping someone would find the answer to this.

It doesn't seem **/usr/bin/startkde** locks desktops as I suspected before. It's weird that it doesn't happen in regular intervals. Sometimes it's a few minutes, sometimes many hours before the lock kicks in. So it can't be the screensaver. Also, I learned that it happens both for sudoers and regular users.

---

### Post by Wyzard on 2006-01-14
I'm seeing the same thing.  It only happens when you use the Switch User option on the Kmenu or the desktop context menu.  It doesn't happen if you use the CNTL-ALT-F# shortcut keys.

I think this is a "feature" of KDE 3.5 -- searching on google shows a few people asking about it, but I haven't found a solution yet.

---

### Post by obibok on 2006-01-14
[QUOTE=Wyzard]I'm seeing the same thing.  It only happens when you use the Switch User option on the Kmenu or the desktop context menu.  It doesn't happen if you use the CNTL-ALT-F# shortcut keys.

I think this is a "feature" of KDE 3.5 -- searching on google shows a few people asking about it, but I haven't found a solution yet.[/QUOTE]

A push in the right direction, Wyzard! I mostly switch among desktops using keyboard shortcuts while my significant other uses the context menu. That's why KDE 3.5 desktop locking would seem to be a random thing.

I really like this feature but it's incomplete... 1) it's easy to bypass using CTRL+ALT+F# (unless you disable the key shortcut in X); and 2) there's nothing (easily found?) to control it.

---

### Post by Wyzard on 2006-01-15
Ok, I found a solution, or at least a workaround.  

This is what's happening:  when the "Switch User" app is used, the /usr/bin/kdesktop_lock command is called with the "--forcelock" parameter to lock the current terminal before switching to the next terminal.  What I did was move the original kdesktop_lock program to a different file named kdesktop_lock.orig and then I created a shell script called kdesktop_lock to call the appropriate screensaver without the locking:

```
cd /usr/bin
sudo mv kdesktop_lock kdesktop_lock.orig 
sudo vi kdesktop_lock

         #! /bin/sh

         # If you are using KDE screensaver, uncomment the following line (remove leading #)
         #kdesktop_lock.orig --dontlock

         # If you are using xscreensaver, uncomment the following line  (remove leading #)
         #xscreensaver-command -activate

sudo chmod a+x kdesktop_lock

```
That should fix the problem, at least in the short term until a better solution can be found.  Of course, any upgrade to KDE will probably overwrite the new kdesktop_lock script, so you'll want to keep a copy elsewhere so you can restore it if necessary.

WARNING: this solution will probably break the KDE screensaver locking completely, so if you need to be able to lock your KDE screensaver you probably don't want to use this fix.  We're using xscreensaver here, so we can always lock the screen using xscreensaver-command -lock.

Hope this helps!  I'll keep looking into a more permanent fix.

---

