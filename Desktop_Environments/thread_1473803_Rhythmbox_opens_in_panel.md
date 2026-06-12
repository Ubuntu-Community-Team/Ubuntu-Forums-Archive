---
title: "Rhythmbox opens in panel?"
date: 2010-05-05
forum: Desktop Environments
---

### Post by bigsmitty64 on 2010-05-05
Hey everyone, In Lucid, I got rid of both gnome panels, and just now remembered that Rhythmbox opens to the top panel by default (at least for me), which means when I opened it I got nothing. How do I change this so that it just opens onto the desktop? I looked in edit/preferences of Rhythmbox but theres nothing in there. Any help is greatly appreciated.
thanks,
Smitty

---

### Post by bigsmitty64 on 2010-05-05
O.K. so I just added a notification applet to my AWN Dock, which makes it so I can use rhythmbox again, but I'm still curious if there is a way to make it open normal instead of to the panel? I would have thought there would be a preference setting in the player itself  :/

---

### Post by russellnation on 2010-09-26
Open the terminal and type 

[HTML]gconf-editor[/HTML]

apps > rhythmbox > plugins > status-icon > window-visible > [SIZE="4"]&#9745;[/SIZE]

---

### Post by wightghost on 2010-09-26
> **russellnation said:**
> Open the terminal and type 

[HTML]gconf-editor[/HTML]

apps > rhythmbox > plugins > status-icon > window-visible > [SIZE="4"]&#9745;[/SIZE]

Thank you for this, I was wondering the same thing.:smile:

---

### Post by bigsmitty64 on 2010-09-26
Wow! Thought this one was dead in the water! Thanks!

---

### Post by Sef on 2010-09-26
> Wow! Thought this one was dead in the water! Thanks!

Sometimes the answer just takes a while.  Glad you got an answer to your problem that was the solution for you.

---

