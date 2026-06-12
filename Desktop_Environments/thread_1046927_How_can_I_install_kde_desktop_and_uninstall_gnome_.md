---
title: "How can I install kde desktop and uninstall gnome desktop from Ubuntu 8.10?"
date: 2009-01-21
forum: Desktop Environments
---

### Post by oblador on 2009-01-21
Hi,

How can I install kde desktop and uninstall gnome desktop from ubuntu 8.10?

Thanks.

PS: If I regret uninstalling gnome desktop how can I get it back and uninstall kde desktop?

---

### Post by x33a on 2009-01-21
first, add this repository to system -> administration -> software sources -> third party software

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

then, type this command in terminal

sudo apt-get install kubuntu-kde4-desktop

and, no need to uninstall gnome.

when the next time you login, select sessions -> kde from login screen choose, make it default.

if you don't like it, make gnome the default desktop :)

---

### Post by reahjw6 on 2009-01-22
In 8.10 kde is already installed.
Go to log out then sessions and use kde as already said above by x33a.

---

