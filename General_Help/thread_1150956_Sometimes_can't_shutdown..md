---
title: "Sometimes can't shutdown."
date: 2009-05-06
forum: General Help
---

### Post by Disabled20240622 on 2009-05-06
I sometimes see this message when shutting down or restarting, about 50% of the time.

[img]http://img56.imageshack.us/img56/9132/img0722medium.jpg[/img]

It appears after my desktop has gone, but before the wallpaper dissapears.

If I click the button, GDM is loaded and I get back to the login screen.

Hardware is an EEE 901, and I have Xubuntu 9.04.

---

### Post by kryptikos on 2009-05-06
Looks like a PAM library issue. There is a bug listed on the Debian forums for similar errors. You have Xubuntu but you chose to use GDM as the display manager? 

From reading the bug reports several people have tied it down to PolicyKit / ConsoleKit. One solution was to purge **libpam-ck-connector** and GDM worked correctly after that. 

The link to the bug report plus comments from the folks experiencing the same issue is here:

[http://www.nabble.com/Bug-525909:-shutdown-with-hal-not-working-td23264188.html]("http://www.nabble.com/Bug-525909:-shutdown-with-hal-not-working-td23264188.html")

(btw...the post keeps adding a smiley face no matter what I try. Where you see the emoticon is actually a ": -" with no space)

---

### Post by 01000111 on 2009-05-08
I have this problem as well.  The solution suggested by the bug report is to purge libpam-ck-connectors, but when I start to do that, synaptic tells me that it will also remove xubuntu-desktop.  I canceled.  So, any suggestions where the cure isn't worse than the problem?

01000111

---

### Post by 01000111 on 2009-05-22
The cause of this is a WinXP server on my network that has a samba share of my Xubuntu system mapped to Z:.  I've change the WinXP machine to map/unmap the share rather than leaving it mapped.  Since then, the shutdown problem has gone away.

I hope this is useful to others.

01000111

---

