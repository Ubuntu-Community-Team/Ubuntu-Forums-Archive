---
title: "remote desktop advice"
date: 2006-07-28
forum: Desktop Environments
---

### Post by acolic on 2006-07-28
Hi,

I have a server which does not have a monitor hooked up to it. I can do most things via SSH.

I'd like to set up the server so that my ubuntu desktop can access it remotely and via a gui environment.

Can someone suggest a good remote desktop type application?

Thanks

Alex

---

### Post by Paerez on 2006-07-28
tightvnc is nice. I use that on my headless server when I am on the LAN.

---

### Post by CarlesOriol on 2006-07-28
You can move your remote X applications with 

ssh user@server -X

-X ports your X to your local machine.

If you want full acces to gnome / kde ... etc Setup XDMCP (you can do it with gksu gdmsetup )

after you can log with

X :1 -query ip_or_servername

or change x for xnest if you want it on the desktop.

---

