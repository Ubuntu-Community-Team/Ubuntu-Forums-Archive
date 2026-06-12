---
title: "I can't believe Pidgin doesn't have this"
date: 2009-02-01
forum: General Help
---

### Post by YMS_1975 on 2009-02-01
I was surprised that nobody posted about Pidgin Internet Messenger's lack of startup options; specifically the ability to launch the program automatically when Ubuntu loads up.

I looked through the menu options for Pidgin but couldn't find it. So that raises another question : Am I able to modify my Ubuntu startup so that Pidgin is automatically started?

---

### Post by tuxxy on 2009-02-01
Yes add it as a session in system > prefs > sessions

---

### Post by YMS_1975 on 2009-02-03
Do you know what the default path for Pidgin is? I can't seem to find it.  


:oops:

---

### Post by kostkon on 2009-02-03
> **YMS_1975 said:**
> Do you know what the default path for Pidgin is? I can't seem to find it.  


:oops:
You don't need the full path. Just put
```
pidgin
```
in the *command* field.

Hope that helps.

---

### Post by YMS_1975 on 2009-02-06
My hat's off to you good sir; worked like a charm!   :D

But it still makes me wonder why this option isn't available straight from the program (and why it has to be added to the start menu). Am I alone in thinking this is a relatively standard feature for such a program? ICQ, MSN & Yahoo have it.

Oh well...either way, it worked! Thanks again bro!

---

### Post by Simian Man on 2009-02-06
> **YMS_1975 said:**
> But it still makes me wonder why this option isn't available straight from the program (and why it has to be added to the start menu). Am I alone in thinking this is a relatively standard feature for such a program? ICQ, MSN & Yahoo have it.


Because that option would have to be implemented differently for each desktop environment/window manager.  Since adding something to a Gnome session doesn't affect KDE, Xfce and so on.

---

