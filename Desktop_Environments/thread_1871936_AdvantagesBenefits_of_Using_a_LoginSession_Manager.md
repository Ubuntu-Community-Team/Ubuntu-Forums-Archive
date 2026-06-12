---
title: "Advantages/Benefits of Using a Login/Session Manager"
date: 2011-10-29
forum: Desktop Environments
---

### Post by Jack Waugh on 2011-10-29
I am running Lubuntu on my portable.  When I say "man lxdm", I am informed that "lxdm  is the LXDE display manager also known as login manager. It shows a graphical login screen for usernames and password and allows  you  to choose  a  desktop and language for the session. After authenticating a user it starts a session.".

I suppose this is being run from /etc/init under instruction of some configs in /etc/init.d or whatever the Debian place is for that sort of thing.

What are considered to be the benefits/advantages of running a session manager rather than having the user log in on a console and run good old "startx"?

Does the session managed by lxdm (or the program doing a similar function on other variants of Ubuntu) have anything to do with running any of the useful daemons such as for example the sound system or some bus?

Is there an overview document somewhere about desktop sessions and how they are configured and started?

---

### Post by gsmanners on 2011-10-29
I think the benefit of a DM is that you don't have to type startx (or some variation on that). It's basically a graphical front-end for startx. Some DMs (like gdm) have several other uses tied into them. It really depends on the DM you use.

---

