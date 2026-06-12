---
title: "Disable GL Desktop for other user"
date: 2007-05-07
forum: Desktop Environments
---

### Post by Ash1984 on 2007-05-07
I enabled a function called 'GL Desktop' in my user account 'ash' and now whenever I log in it restarts immediately back the log in splash screen.

What I need to do is disable the GL desktop item from another users account but I don't know how. Please help.

---

### Post by ayoli on 2007-05-07
when you have enabled this, it's only for your user, antoher users have to enable it to have it if you don't want this configure their menu to hide this option.

---

### Post by Ash1984 on 2007-05-07
I messed up my main account 'ash' by enabling this option. I have logged in as a secondary user 'rachel' and am trying to fix the problem with account 'ash'. 

I have found gconf-editor and the appropriate option under gnome-compiz-preferences with the option 'Enable GL Desktop'

The only problem is I am only able to edit this option for the user 'rachel' whereas I want to edit it for user 'ash'.

Is there any way I can run the 'gconf-editor' command as the user 'ash'?

---

### Post by Ash1984 on 2007-05-07
More specfically in gconf-editor under:

apps>gnome-compiz-preferences

there is an option called 'enable_gl_desktop' which I believe is causing the problem. It is disabled under user 'rachel' but still enabled under user 'ash'. How do I disable this as user 'ash'?

---

### Post by ayoli on 2007-05-07
okay, in a terminal under you 'rachel' acount type in:
```
su ash
```
you'll be prompt for your ash suser pass, then in the same terminal (which now run as 'ash') type in:
```
gconf-editor
```
set your prefs, quit, logout/in under you as account
shoub work.

---

### Post by Ash1984 on 2007-05-07
I thought that would work too though it didn't seem to.

I have now completely uninstalled any package with the word 'compiz' in it and am back into 'ash' account. I'll keep fiddling trying to get some desktop effects to work see how I get on.

---

### Post by Ash1984 on 2007-05-07
SUCCESS!

I reinstalled the compiz packages, and reverted xorg.conf to xorg.conf.original-0 and made the desktop effects work! Very happy now :) Thank you for your support!

---

