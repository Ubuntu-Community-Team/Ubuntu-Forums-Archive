---
title: "No Shutdown Button in Fedora 8 under GNOME"
date: 2008-04-02
forum: Fedora/RedHat and derivatives
---

### Post by Auston on 2008-04-02
Logging in as root and checking control center... system admin... login manager i verified that all users have the ability to shutdown locally

if i then log in as a user in a KDE environment the logoff button gives me the options to shutdown or restart that i want.

however, if i log in as a user in a GNOME environment the logoff button only gives me the option to logoff and then i have to shutdown from the login manager. also using the commands /usr/shutdown or shutdown -h now wont work unless i become root.

is there a setting i have to change as root in a GNOME environment to let all users shutdown the computer from a GNOME environment?

thanks in advance,

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Antman on 2008-04-02
A question for you:
When you start your PC, are you at a text login or a graphical login?

**Edit: Better yet... post the contents of your /etc/inittab file.**

---

