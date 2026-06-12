---
title: "International characters in users &amp; groups"
date: 2006-01-16
forum: Desktop Environments
---

### Post by pelle.k on 2006-01-16
It seems "users & groups" sin "system settings" doesn't like international characters (in my case åäö because i'm swedish).

That's isn't the only gripe it has. Also "secondary groups" in other user i've added doesn't show in the textbox, but only when i choose to "modify user".
I'm still running kde 3.4.3 though...

The former was easy enough to take care of though:

Bash shell seem to handle international characters in USERNAME , but KDE fails to start up. The REAL NAME  can be changed though. Nice when you have a list of user showing in kdm.
sudo usermod -c "new_real_name_with_international_characters" login_name

---

