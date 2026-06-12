---
title: "Running Several Shells"
date: 2012-06-10
forum: Desktop Environments
---

### Post by newb85 on 2012-06-10
So, for a little educational fun, I'm toying with installing several desktop environments on one install of Ubuntu.

I've added gnome, xubuntu-desktop, and lubuntu-desktop.

I'm not sure, though, what the difference is between an xfce session and a xubuntu session.

There's a session option called "Openbox", but it doesn't seem to do anything.  What is it?

I have startup applications that make sense in Ubuntu but not in the lighter variants.  Is there a way to make the startup applications depend on the session?

Suggestions and thoughts are appreciated.

---

### Post by Frogs Hair on 2012-06-10
Open Box [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by newb85 on 2012-06-10
> **Frogs Hair said:**
> Open Box [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Nice.  Considerably outdated, but still helpful as a basic intro.

---

### Post by newb85 on 2012-06-12
A few side effects of installing so many desktop environments:

Duplicate programs: in several cases, I now have multiple programs for doing the same thing.  This is not necessarily bad, as in the case of Gnome-Office and LibreOffice.  On the other hand, having both Ubuntu Software Center and Lubuntu Software Center is definitely unnecessary.  I suspect that all this duplication is slowing my machine a little.

An excessive list of session options on the login screen.  I wish I knew how to block a few of them.

System notification style mix-up.  This didn't happen when it was just Gnome and Ubuntu, but after I installed Lubuntu and Xubuntu environments, system notifications would sometimes be in the style for a different environment.  I suspect this is a bug, but at this point I wouldn't know what to attribute the problem to or where to file a report.

As I mentioned originally, a few of my startup applications for the higher-performance environments don't work or make sense on the lighter environments.  For example, Wallch doesn't work on Lubuntu or Xubuntu (nor would I probably want it to).  If anyone knows how to maintain separate startup app lists, I'd appreciate hearing about it.

---

### Post by hakermania on 2012-06-16
> **newb85 said:**
> For example, Wallch doesn't work on Lubuntu or Xubuntu (nor would I probably want it to).

I just want to let you know that the next version of Wallch will work under many different desktop environments!

---

### Post by ItalOz on 2012-06-17
> **newb85 said:**
> 
As I mentioned originally, a few of my startup applications for the higher-performance environments don't work or make sense on the lighter environments.  For example, Wallch doesn't work on Lubuntu or Xubuntu (nor would I probably want it to).  If anyone knows how to maintain separate startup app lists, I'd appreciate hearing about it.
I've just installed lxde under 12.04 and I'm giving it a go.
So far Unity has sloved down my small asus 1215n while on my older but more powerful Dell inspiron 1525 is doing fine.
I'm also interested  in knowing how to make the different sessions behave differently

---

### Post by newb85 on 2012-08-16
I have found a way to reduce the number of session options available at the login screen.  These come from /usr/share/xsessions.  If you remove one (or put it somewhere else in case you want to restore it), it won't show up on the login screen.

---

