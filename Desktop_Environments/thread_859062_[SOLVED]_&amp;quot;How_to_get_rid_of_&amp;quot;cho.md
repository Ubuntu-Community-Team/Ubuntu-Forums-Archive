---
title: "[SOLVED] &amp;quot;How to get rid of &amp;quot;choose session to restore&amp;quot; after logging in"
date: 2008-07-14
forum: Desktop Environments
---

### Post by offline on 2008-07-14
I tried a mailing list for ubuntu and google but no luck. Whenever I log in in wubi installed xubuntu-xfce 8.0.4.1 (official), there are 2 annoyances I would like to get rid both of these:

a-The "choose session to restore" dialog. You choose the default or any  saved one. Even if there is no saved session with a name the dialog keeps appearing to choose the default to proceed or create new session with a name.

b-When I proceed from a-, "naturally" every firefox, terminal vs I had opened gets restored.

Now, I have the impression that I inadvertantly started this( clicking something in gui, not editing directly) but I am not sure.

Could any one help?

---

### Post by sayakb on 2008-07-14
At a terminal:
```
rm ~/.gnome2/session
```
Also, goto Session Preferences and uncheck "Remember running applications..." under the Session Options tab.

---

### Post by offline on 2008-07-14
> **LinuxIsInnovation said:**
> 

Also, goto Session Preferences and uncheck "Remember running applications..." under the Session Options tab.

Thank you!

---

