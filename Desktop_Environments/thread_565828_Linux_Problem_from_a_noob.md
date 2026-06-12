---
title: "Linux Problem from a noob"
date: 2007-10-02
forum: Desktop Environments
---

### Post by BlazerJoe on 2007-10-02
I got an issue with my Ubuntu, and I think it's something I screwed up and can't fix.  When I fired up my Linux box a few days ago, this is the error I got:

> 
User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.


It let me log in, but I then got this message:

> 
The GNOME session manager was unable to lock the file '/home/joseph/.ICEauthority'.  Please report this as a GNOME bug.  Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is.


Well, I tried doing this, and I got more questions than answers.  Any assistance any of you could provide to a total noob would be greatly appreciated.

---

### Post by zaphod777 on 2007-10-02
try 

sudo chmod 644/home/joseph

see if that helps

---

### Post by aysiu on 2007-10-02
[This](http://ubuntuforums.org/showthread.php?p=2619991#post2619991) might help.

---

### Post by BlazerJoe on 2007-10-02
I'll try both; thanks!

---

