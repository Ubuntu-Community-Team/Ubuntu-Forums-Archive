---
title: "Login Screen"
date: 2006-09-26
forum: Desktop Environments
---

### Post by chickenout on 2006-09-26
Hey guys,  I'm a newbie as far as Ubuntu goes, I hope you can provide some help.

I've installed Ubuntu and everything seemed to be working OK, but now when I boot up the computer, I get the initial login screen.  Fine.  I enter my username and password and the screen changes and I think it is going to work, but then it just reverts back to the login screen.  It does this even if changing the session. 
Is there anyway around this?  Someway to disable the login?

Also, when it was working, the screen resolution got screwy on me and when I tried changing it through the drop down menus, there were no other options of resolution??

Any help would be greatly appreciated.
Thanks

Ok, I can get into the failsafe terminal.  Is there a way to make these changes from here?
Thanks

---

### Post by croak77 on 2006-09-26
Are you using the default Ubuntu install with GNOME and gdm? Are you using Xgl/Compiz? Maybe your xorg.conf was messed up. Try running sudo dpkg-reconfigure xserver-xorg from a terminal. It's a guided setup of X.

---

### Post by chickenout on 2006-09-26
Yeah, thanks.  That is exactly what I ended up doing.  i ran the reconfigure and playing with the settings and it seems to be working now.  Not sure how it got messed up.
It also solved the resolution problem, so I took care of both questions.

Thanks for the response.
:-D

---

