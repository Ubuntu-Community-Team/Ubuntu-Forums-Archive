---
title: "GDM Secure Remote Session Doesn't work"
date: 2009-01-22
forum: General Help
---

### Post by ElvetPuff on 2009-01-22
Hey,

I've set up ssh on my laptop and my netbook and it all works. I used the 'secure remote session' option from GDM once and it worked like a charm - but ever since then it just refuses to work. I get asked for the address of the computer to connect to and then GDM restarts and goes back to the menu.

I can ssh into my laptop from the terminal and from it I run gnome-session successfully (but it doesn't transfer over the themes/background from my laptop, which logging into a secure remote session did).

Any idea how to fix this?

Cheers,

Puff

---

### Post by Dr Small on 2009-01-22
GDM's Secure Remote Session uses some other protocol besides SSH (I forget what it is). Have you installed Firestarter or set any firewall rules on the computer you are trying to connect to?

Edit: Remote Login uses XDMCP

---

