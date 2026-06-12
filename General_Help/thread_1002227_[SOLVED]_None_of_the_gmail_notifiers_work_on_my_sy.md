---
title: "[SOLVED] None of the gmail notifiers work on my system"
date: 2008-12-04
forum: General Help
---

### Post by josephellengar on 2008-12-04
Gnome, Ibex.  None of the gmail notifiers work.  Right now I'm using the one that appears in the applications-internet menu as mail notification.  If I try to give it my username and password it says that they're not valid.  I'm certain that I'm using the correct password.  All of the other ones say essentially the same thing.  I have no idea what is wrong.  Could this be due to my firewall?  What service should I allow to do that?  I'm using the ufw right now.

---

### Post by utsuprainfra on 2008-12-04
are you giving your username as [email]username@gmail.com[/email] ?

---

### Post by josephellengar on 2008-12-04
> **utsuprainfra said:**
> are you giving your username as [email]username@gmail.com[/email] ?

No, but thanks.  I got it to work by enabling a bunch of the protocols in my firewall, but I can't figure out which one it was that works.  Do you know what protocol gmail uses?  I feel a little unsafe with all of them enabled.

---

### Post by lovinglinux on 2008-12-04
> **idigchess said:**
> No, but thanks.  I got it to work by enabling a bunch of the protocols in my firewall, but I can't figure out which one it was that works.  Do you know what protocol gmail uses?  I feel a little unsafe with all of them enabled.

tcp on port 443, which is probably listed as https in the GUFW iptables manager.

---

