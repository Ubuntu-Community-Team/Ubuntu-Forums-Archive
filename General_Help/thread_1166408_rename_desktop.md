---
title: "rename desktop"
date: 2009-05-21
forum: General Help
---

### Post by Gerard08 on 2009-05-21
This sounds like a simple question, but I can't find the answer.  I want to give my desktop-also my home network server- a name.  It appears as "desktop"now. I'm using 8.10. I have a dsl modem and a router.

---

### Post by terrrorr on 2009-05-21
Hi,

Are you talking about host name

- Terrrorr

---

### Post by Gerard08 on 2009-05-23
> **terrrorr said:**
> Hi,

Are you talking about host name

- Terrrorr

Yup, I think so. I can add that info to the //192.168.1.1 screen of my modem/provider info, but I don't know how to let my computer know that. In Windows networking under "system" it is easy to name the desktop. How do I do it in Ubuntu?

Edit: I found a discussion about this: The relevant files are /etc/hostname and /etc/hosts.

I changed the hostname file to my new "hostname" in console and changed the first line under 27.1.1.1 to the new name, but I went through the grub- safe startup-command line:```
nano -Bw /etc/hosts
```Everything is working OK.

---

