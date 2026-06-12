---
title: "Home drive has wrong permissions"
date: 2005-10-21
forum: Desktop Environments
---

### Post by vahju on 2005-10-21
While I was installing nwn, see this [thread]("http://nwn.bioware.com/forums/viewtopic.html?topic=455232&forum=72") for solution, I accidentally changed permissions and possible ownership of my home directory on the account I login (which is guest).

I am sure the solution has something to do with chmod and chown commands but I am not familiar enough to solve on my own.

I know what I did that caused the issue.  During one of the many attempts at installing nwn in the terminal I forgot to cd into nwn before doing chmod and chown commands.  So now when every I login as guest I get the message that home directory has wrong permissions.  I just click through the message and get to the desktop and nothing else seems to be affected.

I am definitely learning as I go along and fix issues.  Thanks ahead of time for any help.

---

### Post by migueljacq on 2005-10-21
[QUOTE=vahju] So now when every I login as guest I get the message that home directory has wrong permissions.  I just click through the message and get to the desktop and nothing else seems to be affected.[/QUOTE]

Was it an error about .dmrc permissions?

---

### Post by migueljacq on 2005-10-21
Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=72988](http://ubuntuforums.org/showthread.php?t=72988)

---

### Post by vahju on 2005-10-24
[QUOTE=migueljacq]Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=72988](http://ubuntuforums.org/showthread.php?t=72988)[/QUOTE]

Thanks for link.  This would have worked well if I used chmod to 644 instead of what mentioned in that thread.  This comprised that folder then when I tried to change it back I couldn't due to permissions.  I received errors no matter I did so I took this as a newbie lesson and reloaded.

Moral of this story.  Chmod to what is in the error message not on other posts and also pay attention to what directory your in when doing this command.

Wrong directory = reload of system

Problem is solved so this post can be closed.

---

### Post by migueljacq on 2005-10-24
Fair enough. I found the chmod 644 didn't fix the issue but most people I spoke to found that chmod 700 did. So, whatever works :-)

---

