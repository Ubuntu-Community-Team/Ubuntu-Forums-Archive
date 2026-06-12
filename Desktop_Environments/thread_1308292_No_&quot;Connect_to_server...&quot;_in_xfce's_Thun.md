---
title: "No &quot;Connect to server...&quot; in xfce's Thunar. Ideas?"
date: 2009-10-31
forum: Desktop Environments
---

### Post by osjak on 2009-10-31
Hi All,

I have been using Gnome on my desktop and had many different server connections bookmarked in Nautilus file manager. That was a handy way to connect to servers of different types - ftp, ssh, scp-only etc. I didn't have to have different clients for different types of connections, everything was done in Nautilus.

Yesterday I have switched from Gnome to xfce. I love how my old desktop feels light and alive. I am trying to figure out a simple way to set up those server connections, but the Thunar file manager xfce uses does not have the "Connect to server..." functionality built in as Nautilus does. I am sure I am not the first person to deal with this. Searching does not produce anything useful. Can anyone point me in the right direction please? Is there a way in xfce to have all types of server connections pre set in the file manager?

Thank you.

EDIT: My desktop - Ubuntu 9.04, xfce4

---

### Post by Ugluk on 2009-11-01
You cannot, because Dolphin do not use GnomeVFS. You have to mount the share first via cifs or nfs.

---

