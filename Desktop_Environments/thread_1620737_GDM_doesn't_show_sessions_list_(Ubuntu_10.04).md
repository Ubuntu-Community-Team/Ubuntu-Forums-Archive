---
title: "GDM doesn't show sessions list (Ubuntu 10.04)"
date: 2010-11-13
forum: Desktop Environments
---

### Post by dejanc on 2010-11-13
Hello all,

When I log out of the current user and get to the GDM login screen, the only options, apart from selecting the user, are "Accessibility options" and Shutdown/restart menu.

I can't choose  session (gnome, KDE, etc.) or language.

This is my /etc/gdm/custom.conf:
[daemon]
AutomaticLoginEnable=false
AutomaticLogin=user
TimedLoginEnable=true
TimedLogin=user
TimedLoginDelay=3
DefaultSession=gnome

I'm logging in without a password (I can't remember where I set it up like that, but local login doesn't require a password).

Does anyone know how to get sessions option in the login screen?

It gets a bit more complicated. On the initial GDM login screen, when those TimedLoginDelay=3 seconds are running out, I can see the options to change session, but not when I log out of the current user.

Thanks for any tips & help
Dejan

---

### Post by dejanc on 2010-11-13
> **dejanc said:**
> 
I'm logging in without a password (I can't remember where I set it up like that, but local login doesn't require a password).


And, there is my problem! I reenabled passwords on login, so now, when I select the user, the next screen asks me for my password and all other things I need (session, language, etc.).

Still, does anyone know how to get around this and still be able to choose DE without having to login with a password?

---

