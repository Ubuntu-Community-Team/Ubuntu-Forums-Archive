---
title: "Desktop Environment gone haywire - big time"
date: 2007-04-26
forum: Desktop Environments
---

### Post by netsurfau on 2007-04-26
When I booted up my 'puter and logged in, I had the following issues.

1. The workspace switcher is only showing as a tiny line (about same size as a separator).
When I go in to preferences it now shows only one workspace. Changing to two makes no
difference to it's current appearance & after a re-boot, it changes back to one workspace.

2. While an application is loading, it shows in task bar but, once it's up & running, the task
bar does not show it and it remains blank.

3. Any application I open is missing the top bar for the "window". ie; the bar that contains the
no app title or the minimise, maximise and close buttons. Also, the open app covers the menu
bar at the top of the desktop so, I cant access any other app or even the log out, without closing
the currently open application.

Any ideas on what has happened or a fix?? I upgraded to Feisty day after it was released.

---

### Post by dbott67 on 2007-04-26
Try creating a new user account and logging in as that user.  If everything looks good, then we know it's something in your profile.

Are you running Gnome, KDE, XFE?

-Dave

---

### Post by netsurfau on 2007-04-26
I logged out & back in as root.  The workspace switcher was back.

Using standard Gnome environment.


Is there a way to repair my profile or, will I have to blow it away & create a new one?

---

### Post by llamakc on 2007-04-27
What do you mean by "profile"? You can delete the contents of the .gnome2 .gconf .gconfd .gnome .gnome2_private directories and that will get you right back to a default install's version of Gnome.

---

### Post by netsurfau on 2007-04-27
By profile, I mean my user account/profile. The files that have my individual settings.

This problem obviously is somehow related as it is only affecting my main log in 
.

---

### Post by netsurfau on 2007-04-27
This is supposed to be the fix
[http://ubuntuforums.org/showthread.php?p=2544698#post2544698](http://ubuntuforums.org/showthread.php?p=2544698#post2544698)

Has worked for others but, knowing my luck it may not.

---

### Post by dbott67 on 2007-04-27
> **llamakc said:**
> What do you mean by "profile"? You can delete the contents of the .gnome2 .gconf .gconfd .gnome .gnome2_private directories and that will get you right back to a default install's version of Gnome.

This is what I meant by profile (the .gnome* & .gconf dirs mentioned by llamakc).  I didn't mention deleting those directories in my first post for a couple of reasons:

1. I didn't know if netsurfau was running Gnome or KDE, etc. (and I don't know what the equivalent KDE/XFCE directories are).
2. If logging in under a new user didn't cure it, then it's probably not related to the .gnome* & .gconf* directories.

@netsurfau: Try moving/renaming the directories listed by llamakc and then log back in as your regular user.

-Dave

---

