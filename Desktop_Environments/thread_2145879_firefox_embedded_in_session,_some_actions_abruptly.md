---
title: "firefox embedded in session, some actions abruptly end session"
date: 2013-05-16
forum: Desktop Environments
---

### Post by jcoles on 2013-05-16
I'm running xubuntu 13.40, which has been generally well-behaved since I installed it a week ago.

Suddenly today, every time I log on, firefox starts. It's not in the auto-start session list. and session save is not enabled. 

There are several actions that can cause the session to end abruptly, dropping me back to the logon screen:

[LIST]
[*]in firefox, double-click a downloaded item to view 
[*]select Settings > Session and Startup from the menu
[*]select the session menu (top right, has user's name on it), no chance to choose anything
[*]editing a text file (selected in Thunar) - ridiculous instability!!!
[/LIST]
 
Any ideas how to fix this, or at least begin investigating why it happens?

---

### Post by dentaku65 on 2013-05-17
Did you tried to delete the sessions?
```
rm -Rf $HOME/.cache/sessions
```

---

### Post by jcoles on 2013-05-17
Thanks, dentaku65. Firefox no longer starts with the session. And the stability problems appear to be solved too. Another one for my notes.

---

### Post by epikvision on 2013-05-17
Be sure to mark the thread as [solved] when you're satisfied with the solution.

---

