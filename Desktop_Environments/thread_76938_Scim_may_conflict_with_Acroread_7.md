---
title: "Scim may conflict with Acroread 7"
date: 2005-10-15
forum: Desktop Environments
---

### Post by realwhz on 2005-10-15
Hi,

I have just installed Ubuntu 5.10.  It's so wonderful.

But I found some problems about acroread and scim.  I installed
acroread from multiverse.  It works well.  But after I installed scim,
acroread refused to work.  I mean, even when I start it from command
line, nothing happened.  Not any error messages were returned.

Since the installation of scim will cause many other packages to be
installed, including:
libanthy0 libm17n-0 libotf0 m17n-db m17n-env menu scim
scim-config-socket  scim-frontend-socket scim-gtk2-immodule scim-m17n
scim-server-socket
I can not make sure which package(s) really results in this problem.  In fact, no matter if I have set the variables, say, XMODIDIERS to enable scim, this problem always exits.

Have anyone encountered the same problem?

Thank you very much.

---

### Post by Abiezer on 2005-10-16
I had a similar problem with it conflicting with RealPlayer. I started from a console, found the error message and after Googling found [this page]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started") at the SCIM homepage which addresses the issue and offers a workaround. I hadn't actually tried Acrobat until I read it, but found the same problem as you. Appending the line he gives to the startup script fixed it too. Hope that helps.

---

### Post by realwhz on 2005-10-16
Thank you, Abiezer :) 

It really works!  Then I can use scim, my favorite input method framework again.

---

