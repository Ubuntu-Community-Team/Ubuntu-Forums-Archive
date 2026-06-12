---
title: "VNC logs?"
date: 2009-03-08
forum: General Help
---

### Post by dmillerw on 2009-03-08
Lately I've been getting mysterious VNC connection requests, but I cannot figure out where there coming from.

Does Ubuntu store connection logs anywhere?

If not, does anyone know of a way to trace them?

---

### Post by LegendofTom on 2009-03-08
I would check in /var/log/ or maybe in .vnc somewhere

---

### Post by dmillerw on 2009-03-08
anyone?

---

### Post by dmillerw on 2009-03-13
Anyone?

---

### Post by Wiley99 on 2009-04-10
> **dmillerw said:**
> Lately I've been getting mysterious VNC connection requests, but I cannot figure out where there coming from.

Does Ubuntu store connection logs anywhere?

If not, does anyone know of a way to trace them?

You can check /var/log/auth.log for general access attempts to your computer. 

Or you can open Firestarter (if you're running it), block the port and check who's trying.

A tip: don't open any ports for vnc but go through ssh. And for ssh, don't use the standard port 22 but something 'unknown' above 1000 or so.
Links: ssh: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
vnc through ssh: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

