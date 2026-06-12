---
title: "Admin tools to run under desktop environment?"
date: 2008-01-25
forum: Desktop Environments
---

### Post by KimTas on 2008-01-25
Hi,

I am new to linux - and have just installed Ubuntu 7.10 Server onto an old Proliant Server. As I'm not familiar with the command line yet - I've also installed the Desktop GUI.

I am wanting to configure Apache, PHP and MySQL. Are there any essential applications I should install under the desktop GUI to administer these? Any other administrative tools that I should install?

Also - how do I give the user that I created during the install full admin privileges to install software on the machine?

Cheers,
Kim

---

### Post by kidders on 2008-01-26
Hi there,

All of these things are highly inadvisable, to be honest. Installing a graphical environment on a server imposes a performance penalty & creates security issues. Using fancy tools to reconfigure services can cause reliability problems, and giving users full admin privileges will (more or less) turn your server into a time bomb.

The furthest I would suggest you go would be to install utilities like Webmin, phpMyAdmin, and so on ... things that don't require a server-side graphical environment anyway. The best way to work full-time with administrative privileges is probably to discard your unprivileged account and log in as root instead ... but it's difficult to overstate how bad an idea that is, particularly when a graphical environment is involved.

---

