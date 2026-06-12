---
title: "Restart Unity Desktop without logout"
date: 2012-02-12
forum: Desktop Environments
---

### Post by javasharp on 2012-02-12
Hi, 

I am new to Ubuntu. I use Ubuntu 11.10. 

I am experiencing problems with unity, sometimes launcher does not respond and minimize-maximize buttons disappears. 

In such cases i used restart explorer.exe in Windows. 

**I wonder if there is a way to restart unity in Ubuntu 11.10**

Thanks in advance.

---

### Post by Krytarik on 2012-02-13
> **javasharp said:**
> ... and minimize-maximize buttons disappears.
Indicated by this, I presume you are using the regular Unity, not Unity 2D; in this case, you can simply restart Compiz - of which Unity is a plugin - preferably via the Alt+F2 dialog if that still works then, or via a launcher you can create on your desktop, but if doing that from a Terminal, prepend "setsid" to the command:
```
compiz --replace
```Regards.

---

### Post by Corelogik on 2012-12-13
I know this thread is old, but thank you. That's exactly what I was looking for. My DE got a little unresponsive after tweaking some Compiz settings.

---

