---
title: "Environment variables and gnome-panel"
date: 2005-07-15
forum: Desktop Environments
---

### Post by Athropos on 2005-07-15
Hi,

I want to have some environment variables set for an application I launch from the gnome-panel. I tried to simply set them in my .bashrc, but applications launched from there do not seem to see them. However, if I launch a terminal and then start my application from this terminal, the variables are set.
Does someone knows where I can set these variables to make them available to the applications launched from the panel?

---

### Post by mad_scientist03 on 2005-07-15
I don't have much experience with Ubuntu (I am from the Fedora world), but I believe the environmental variables should be set in .bash_profile. You can try logging out, logging back in, and those variables should be global to your username.

---

### Post by Athropos on 2005-07-15
Hi,

Thanks for your help, but this does not work. I tried setting my variable in .bash_profile, killed X (Ctrl-Alt-Backspace) and logged in again, but my application still doesn't see the variable...

---

### Post by richi on 2008-07-21
In the jungle of bash files(~/.bashrc, ~/.bash_profile, ~/.profile,  /etc/profile, /etc/bashrc, /etc/bash.bashrc ... beyond comprehension by a mere mortal), I found that environment variables defined in **/etc/profile** were visible by applications launched by the gnome panel, so a possible solution is to place your envt vars in that file. The only downside is that this file is system wide, i.e. common to all users, so these vars will be visible by all.

---

