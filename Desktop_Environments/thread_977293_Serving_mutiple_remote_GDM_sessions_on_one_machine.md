---
title: "Serving mutiple remote GDM sessions on one machine"
date: 2008-11-10
forum: Desktop Environments
---

### Post by Heiliger on 2008-11-10
Hi,

how can I serve multiple GDM sessions (different users) on one machine?

The setup:

one server:
hosting multiple GDM sessions (different users)

the clients:
each client (different users) is running X and is displaying a remote session that is running on the server. The full GDM desktop is visible.

How I plan to do it:
running X on each client
using ssh with X forwarding (on the client something like: ssh -X user@serverip 'gnome-session')
starting gdm via ssh on the server for each client and each user

How can I start several gdm sessions on the server? Any suggestions?

_ Heiliger _

---

