---
title: "vncserver and gtksudo"
date: 2005-12-06
forum: Desktop Environments
---

### Post by lean on 2005-12-06
Hello, I have installed ubuntu-desktop on a server, and are connecting to it through a vncserver (not a shared desktop, the server only have console output).

The vncserver starts gnome-session.

When I try to go to a menu, and do an administrative task I get the following message:

"Failed to run /usr/bin/gnome-language-selector as user root:
 No password was supplied and sudo needs it."

What to do about that? It is propably a service that needs to be started, maybe something missing in gnome-session?
It could also be that vncserver doesn't support the switching to user root or something.
Anybody know what to do?

---

### Post by lean on 2005-12-06
Found the error, the /etc/sudoers file was broken.

---

