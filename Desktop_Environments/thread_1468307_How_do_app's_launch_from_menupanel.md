---
title: "How do app's launch from menu/panel?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by drreed on 2010-05-01
There is something going on that I don't really understand. In some desktop environments (I think Xubuntu Xfce4 is one,) when I right click on a "launcher" and choose properties, there is a "command" line string that I've prefixed with sudo because the program wasn't smart enough to prompt me for a password if I didn't (and would fail).

In 9.10 and now 10.04 w/ Gnome - I've had mixed results. It wasn't letting me modify my ssl certificates, so I took it offline and tried to run firefox as root from the panel, to see if that was the problem. The browser won't launch. 

I did modify my security certificates, and removed sudo from the panel launcher. My question is:

Why didn't the browser launch with sudo prefix?

---

### Post by P4man on 2010-05-01
First of all, you should never ever ever run a browser with (gk)sudo. Ever.
How much easier do you want to make it for malicious sites to attack your pc?

if something aint working, lets fix it, but do not run firefox as root to browse the web.

Im hesitant to give the answer to your question, as I fear you will just apply this quickfix, because you *can* do it, but its really a horrible idea.
Anyway.. all graphical programs you want to run as root, prefix them with gksudo, not sudo (kdesu on KDE). please just dont do that for a browser and tell us what the problem is running the browser under your own account.

edit: I misread and was a bit quick to respond as you did the right thing, taking the machine offline. Pfew. Warning still applies, but clearly you are aware already :)

---

### Post by drreed on 2010-05-01
> **P4man said:**
> First of all, you should never ever ever run a browser with (gk)sudo. Ever.
How much easier do you want to make it for malicious sites to attack your pc?

if something aint working, lets fix it, but do not run firefox as root to browse the web.

Im hesitant to give the answer to your question, as I fear you will just apply this quickfix, because you *can* do it, but its really a horrible idea.
Anyway.. all graphical programs you want to run as root, prefix them with gksudo, not sudo (kdesu on KDE). please just dont do that for a browser and tell us what the problem is running the browser under your own account.

edit: I misread and was a bit quick to respond as you did the right thing, taking the machine offline. Pfew. Warning still applies, but clearly you are aware already :)


Hehehe . . . it's probably a safety feature, but I'm just not aware of it

Maybe I did use gksudo before . . .(but it wasn't for a browser or irc!)

---

