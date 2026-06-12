---
title: "User-switching using &quot;new login&quot; doesn't really work"
date: 2005-11-20
forum: Desktop Environments
---

### Post by kmonihen on 2005-11-20
Hi,
  I've searched around for a way to do user-switching similar to Windows (maintaining processes/windows across sessions), and have found forum posts and other resources that say the "new login" program does this.

The problem is that it doesn't do this for me.  What I get is that the first time I switch users it goes to the login screen and I log in as a different user (this is OK).  But switching back to the other user just takes me to a console-type login screen (says "breezy... tty" at the top).  When I log in as the other user it doesn't start my KDE session up again.  When I run "startx" it just starts a new session.  At this point I'm stuck because I can never get back to the login screen and have to shutdown.

Any help with this would be appreciated. =]

BTW, I'm using Breezy with KDE.

Thanks,
Keith

---

### Post by 23meg on 2005-11-21
Try hitting Ctrl+Alt+F7 when you end up at the command prompt.

---

### Post by kmonihen on 2005-11-21
[QUOTE=23meg]Try hitting Ctrl+Alt+F7 when you end up at the command prompt.[/QUOTE]

Thanks for the advice, but when I try this I get a blank screen.  If I try Ctrl-Alt-F9 I can usually get the graphic login screen again, but logging in just creates a new KDE session.  Any other Ctrl-Alt-Fx just takes me to the login screen for another TTY session.

-Keith

---

### Post by Alexander Kirillov on 2005-11-22
[QUOTE=kmonihen]Hi,
  I've searched around for a way to do user-switching similar to Windows (maintaining processes/windows across sessions), and have found forum posts and other resources that say the "new login" program does this.

The problem is that it doesn't do this for me.  What I get is that the first time I switch users it goes to the login screen and I log in as a different user (this is OK).  But switching back to the other user just takes me to a console-type login screen (says "breezy... tty" at the top).  When I log in as the other user it doesn't start my KDE session up again.  When I run "startx" it just starts a new session.  At this point I'm stuck because I can never get back to the login screen and have to shutdown.

Any help with this would be appreciated. =]

BTW, I'm using Breezy with KDE.

Thanks,
Keith[/QUOTE]


You better ask this question in Breezy forum - the forum you are posting to right now is for Hoary users, and Hoary doesn't have this feature.

---

