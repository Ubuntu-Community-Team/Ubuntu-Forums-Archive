---
title: "window too big"
date: 2005-12-29
forum: Desktop Environments
---

### Post by Titus A Duxass on 2005-12-29
I am trying to add another user, when I open the Users & Groups window in system settings I cannot see the Administrator button.

This same thing occurs with several other admin tasks, the window is too big.

---

### Post by infoseeker on 2005-12-29
Use:

> #sudo kcontrol

---

### Post by Titus A Duxass on 2005-12-29
Using sudo kcontrol provides an alternative way of achieving a solution for the User problem.
But it does not give me help in solving my problem.

Please do not suggest work arounds, I would like to know if there is a known problem with regard to window sizing.

---

### Post by jamboarder on 2005-12-29
[QUOTE=infoseeker]Use:[/QUOTE]
Run Command:
  "kcontrol",  first and to see if the Administrator button shows up.

If it doesn't work then run:
  "kdesu kcontrol"

Other's on here have report issues surrounding the use of sudo with kcontrol.  In fact for any root stuff in KDE I recommend using kdesu.

Yes it is a known problem.

Hope this helps.

---

### Post by GeneralZod on 2005-12-29
[QUOTE=Titus A Duxass]

Please do not suggest work arounds, I would like to know if there is a known problem with regard to window sizing.[/QUOTE]

Yes there is:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=18203](http://bugzilla.ubuntu.com/show_bug.cgi?id=18203)

The provided workaround is probably your best course of action.

---

