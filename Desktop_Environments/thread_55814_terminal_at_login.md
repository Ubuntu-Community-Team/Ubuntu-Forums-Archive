---
title: "terminal at login"
date: 2005-08-10
forum: Desktop Environments
---

### Post by hunteramor on 2005-08-10
ubuntu has gotten into the habit on my machine of launching a terminal window every time i log in.  it's not in sessions/startup and it's not because of a saved session.  any other ideas as to what might be causing this problem?  thanks!  been working on it for a couple of days now to no avail.  wouldn't be surprised if it's something incredibly stupid.    ](*,)

---

### Post by Holdem on 2005-08-10
So have you shut-down with everything closed and saved that as a session. It might clear it.

---

### Post by hunteramor on 2005-08-10
i tried that, to no avail.  of course, the reason it didn't work was because i didn't do it properly.

i use a [transparent terminal](http://www.ubuntuforums.org/showthread.php?t=38938) , minimized to the tray.  evidently, 'saving the session' doesn't 'save' the position of each window, like i thought it did (or at least not when it involves alltray).

i wound up deleting the tterm start command from sessions/startup, exiting out of the running tterm, and then logging out while saving.  problem solved.  replaced tterm in sessions/startup, no problems on subsequent logins.    \\:D/ 

thanks for the suggestion.  annoying problem solved!

---

