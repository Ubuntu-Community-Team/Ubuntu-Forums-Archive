---
title: "How to show network status in GDM"
date: 2010-10-05
forum: Desktop Environments
---

### Post by double1116 on 2010-10-05
I'd like to show network status in GDM. The use case is that I have a laptop configured with nis. The wireless NIC it has takes a while to bring up. So I'd like to show some indication on GDM what the network status is so the users know when to login.

I'm expecting to add something to /usr/share/gdm/autostart/LoginWindow but I'm not sure what would be appropriate.

Ideas?

---

### Post by Frogs Hair on 2010-10-05
There are some network activity monitors in the repository you may want to look at if you haven't already .

---

### Post by mister_p_1998 on 2010-10-06
Gdesklets? thats what I use.
Steve

---

### Post by double1116 on 2010-10-10
> **mister_p_1998 said:**
> Gdesklets? thats what I use.
Steve

Tried that but gdesklets is broken on Lucid. I tried the sysmonitor in screenlets, but it locks up if the wireless goes offline :(

Maybe I'll use screenlets and write my own...

---

