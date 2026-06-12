---
title: "KDE won't go away..."
date: 2007-05-16
forum: Desktop Environments
---

### Post by Th3Sourc3 on 2007-05-16
After following Ubuntu linux for around two years, I finally decided that when I bought a new laptop, it would become my primary OS.  After debating with myself over what version (Xubuntu, Kubuntu, or plain Ubuntu) I'd install, I finally decided on the Gnome version.  

Last night, I began to rethink whether or not I should have gone that way after finding that many apps I want are not exactly fully compatible with Gnome (Kopete's sound notifications don't work, for a small example.)  So I ran an apt-get install for Kubuntu-desktop.  It installed and worked perfectly.  I decided, though, that kde just isn't for me.  

This morning, I did apt-get remove Kubuntu-desktop, logged out, apt-get autoremove, logged out, then apt-get install ubuntu-desktop to attempt to switch back to the GDM that was working better for me.  The problem is that the login screen, the OS load bar, and some of the splashes are still the same.  I tried to change the login by going to  System->Admin->Login, and while running a Gnome environment, it errored "GDM is not running,"  

Something from KDE remains on the system and I'm not sure what to do...

---

### Post by taurus on 2007-05-16
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Th3Sourc3 on 2007-05-16
> **taurus said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
That was the very first thing I tried.  When I try it again, it returns 0 packages to be uninstalled/removed.  Kubuntu's gone, but GDM won't come back.

EDIT: Come to think of it, the first time I tried, it crashed.  I'll try again now.

---

### Post by Th3Sourc3 on 2007-05-16
Beautiful.  Worked perfectly that time.  I guess when the KDE daemon said it stopped, it really didn't.  This time I chose NO when it asked, and the install worked wonderfully...

It did delete Pidgin, though... Off to reinstall.

Thank you very much!

---

