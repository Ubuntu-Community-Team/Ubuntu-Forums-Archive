---
title: "Xubuntu 13.10 always saving session"
date: 2013-12-03
forum: Desktop Environments
---

### Post by dave72 on 2013-12-03
Since the upgrade to Xubuntu 13.10 (from 13.04), every time I logout my  session is saved. I have checked in settings and verified that save  session is not selected and I make sure that the save session tick box  on the logout dialogue is also unticked.

I suspect this is a bug, as it also does it on my work PC & laptop.  It is quite an annoying one as when I login I have to wait for a dozen  windows that I don't want, to load. I have been unable to find a mention  of anyone else having the same problems via google.

The best work around I can think of is to clear out ~/.cache/sessions  via a startup script. Does anyone know if a less-dirty fix?

---

### Post by Toz on 2013-12-03
Hello and welcome to the forums.

How are you logging out? Sessions menu, action buttons plugin, menu logout, terminal command, etc? The reason I ask is that there appears to be some inconsistency in Xfce with respect to session management. See [this thread]("http://forum.xfce.org/viewtopic.php?id=8082") on the Xfce boards for some more information and possibly related bug reports.

Seems the "Log out..." session menu or the Logout option on the Main menu do respect the session settings. The action buttons or "Logout" session menu don't.

---

### Post by vasa1 on 2013-12-03
> **Toz said:**
> ... See [this thread]("http://forum.xfce.org/viewtopic.php?id=8082") on the Xfce boards for some more information and possibly related bug reports.
...
That link suggests that there maybe some functional differences depending on which session exhibits the problem: Xfce or Xubuntu. It would be nice if OP adds that information.

---

### Post by Toz on 2013-12-03
> **vasa1 said:**
> That link suggests that there maybe some functional differences depending on which session exhibits the problem: Xfce or Xubuntu. It would be nice if OP adds that information.

I'm not sure its related to the session (xfce vs xubuntu), as I think both would be affected, as much as it is related to the methods used to logout. It looks like the various Xfce components may be using different methods.
- Application menu logout command
- Session menu plugin multiple logout methods ("Logout...", "Logout", "shutdown")
- Action buttons plugin

At least that's how I'm understanding it.

---

### Post by vasa1 on 2013-12-03
> **Toz said:**
> I'm not sure its related to the session (xfce vs xubuntu), as I think both would be affected, as much as it is related to the methods used to logout. It looks like the various Xfce components may be using different methods.
- Application menu logout command
- Session menu plugin multiple logout methods ("Logout...", "Logout", "shutdown")
- Action buttons plugin

At least that's how I'm understanding it.
Okay! I've always used the first one you listed (and removed the other two from my panel).

---

### Post by dave72 on 2013-12-04
Thanks for the feedback. I was mainly using the action buttons but now I come to think of it, I rarely just logout and usually shutdown (via the action buttons).

I tried a logout from the main menu, which did restore my session, but did not after I deleted .cache/sessions/*, opened a few random windows and logged out with the main menu. I will try shutting down via the command line for a couple of days and see if the problem persists.

---

### Post by andy-aka-fish on 2013-12-07
I've been having the same problem. I usually shutdown using the user menu on the panel - the one that shows your username and when you click it there are options for logging out and shutting down, etc. I sometimes log out via that menu instead of shutting down, and sometimes my session is not restored. However,  I can't remember which method restores the session on the next login, but I suspect it happens when shutdown is used. It doesn't happen every time, though, so maybe I've shutdown in other ways without realising it.

---

### Post by ovocean2 on 2013-12-19
This bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1204919"). It hasn't drawn a lot of attention.

---

