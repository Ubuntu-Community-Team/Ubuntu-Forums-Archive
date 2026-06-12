---
title: "login loop"
date: 2005-05-08
forum: Desktop Environments
---

### Post by punkass on 2005-05-08
hi all, i have a buddy of mine that is running hoary, and he just moved away...he now says that when he enters is username and password in gdm it accepts it, pauses, then returns to gdm without error, and never logs him in.

I got him to try Ctrl-Alt-Fx to a different terminal and he his able to log in fine.

any thoughts?

---

### Post by dave9191 on 2005-05-08
It could be any number of things. Probably a bad X config. I once updated my drivers and X would crash as soon as I tried to log in sending me back to the login screen with an error message.

---

### Post by alastair on 2005-05-08
It will probably be some problem starting the desktop. You might find the problem by looking in the session error file e.g. ~/.xsession-errors.

---

### Post by thoms on 2005-05-09
Interestingly, this only happened to me when I tried to log in to root once (without root access setup/configured) if that's any help.

---

