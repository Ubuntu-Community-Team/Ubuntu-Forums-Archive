---
title: "xdg-open smb"
date: 2011-05-03
forum: Desktop Environments
---

### Post by alpxp on 2011-05-03
I have 
alpxp@alpxp-laptop:~$ gconftool-2 --get /desktop/gnome/url-handlers/smb/command
/usr/bin/nautilus %s
but:
alpxp@alpxp-laptop:~$ xdg-open smb://10.55.80.128/Video/
Error showing url: The specified location is not mounted
why is it so?

alpxp@alpxp-laptop:~$ /usr/bin/nautilus smb://10.55.80.128/Video/
works perfect

I figured that this is the problem why my browser does nothing if I click to the smb:// urls

---

