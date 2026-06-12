---
title: "Network Manager"
date: 2009-05-22
forum: General Help
---

### Post by BslBryan on 2009-05-22
Hello, everyone. :-)

Do me a favour, and hover your mice over the NetworkManager applet on your panel (where your internet connections are shown). 

An example response is a display that looks like this:
Wireless network connection to 'NETGEAR' (99%).

Does anyone know how this is possible?

I looked around in the source code, but couldn't find anything relevant.  What I'm trying to do is display that same text alongside the NetworkManager, for ease of use.  :-)

---

### Post by cariboo on 2009-05-22
What you are looking for is called a tool tip, look in python-notify and libnotify, as it is part of the system wide notifications.

---

### Post by BslBryan on 2009-05-22
Hmm...  No dice.  Can't seem to find any UTF-8 files to edit.  Seems like throwing up that text would be a simple command, wouldn't you think?

---

### Post by BslBryan on 2009-05-23
Bump. :-)

After doing some Googling, it seems that with CompizConfig, I can change how the tooltips display, but I'm more interested in what makes the tooltip work, so I can use that knowledge to add the tooltip as text on the Ubuntu panel.

Any other ideas?

---

