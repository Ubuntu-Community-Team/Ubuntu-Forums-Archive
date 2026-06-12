---
title: "Multiples instances of the same process?"
date: 2006-01-08
forum: General Help
---

### Post by niviche on 2006-01-08
Hello

Using KDE 3.5 final on Kubuntu Breezy and nothing really funky on my machine.

Running Ksysguard, I just noticed that I have some processes running more than once at the same time:
-4 x Apache2
-6 x Getty (what is this anyway?)
-5 x kio_http
-6 x spamd (this might be a bit exaggerated)
-2 x sudo

These process do not seem to be taking up resources, but if this was on Windows, I would be screaming fire and trying to terminate most of them. Being newbie to Linux, I however don't know how much of a problem it is.

My PC is not extremely powerful, and I'd rather not have things running which I do not need. Can anybody tell me how to clean this mess up?

Thank you.

Nicolas

---

### Post by Manny C on 2006-01-09
Hi Nicholas

If you don't used apache2 and spamd (ie. Server software and mail filter), uninstall their related packages. I don't have them running on my system.

```
 sudo apt-get remove apache2 spamassassin 
```

---

### Post by niviche on 2006-01-09
[QUOTE=Manny C]If you don't used apache2 and spamd (ie. Server software and mail filter), uninstall their related packages.[/QUOTE]

I need Apache2 to run a small LAMP server, and I need Spamassassin to filter the spam email in Kmail. However, I need them only once, not four or six times. :-/

---

