---
title: "How do I switch to root? (Not in terminal)"
date: 2008-12-23
forum: General Help
---

### Post by Aizawa on 2008-12-23
I need to copy a few files from one folder to another, but my non-root user doesn't have permission to move them. So far I just do it in terminal, but is there a way to switch to root in the.. "graphical environment"?

---

### Post by albandy on 2008-12-23
You can open nautilus with super user permisions
sudo nautilus

---

### Post by Aizawa on 2008-12-23
Thanks!

---

### Post by Pobega on 2008-12-23
> **albandy said:**
> You can open nautilus with super user permisions
sudo nautilus

gksudo is the preferred way to get sudo in a GUI. So, *gksudo nautilus*

---

### Post by stchman on 2008-12-23
> **Aizawa said:**
> I need to copy a few files from one folder to another, but my non-root user doesn't have permission to move them. So far I just do it in terminal, but is there a way to switch to root in the.. "graphical environment"?

Using the gksudo nautilus is certainly the easiest way.  NEVER log in as root as you will bypass all the security features of Linux.

What files are you copying.  I find that there is almost never a need to copy files to protected areas of the OS.  You don't need sudo for your home.  If you setup another partition then to copy files you will need to change ownership of the partition.

---

### Post by Pobega on 2008-12-23
> **stchman said:**
> Using the gksudo nautilus is certainly the easiest way.  NEVER log in as root as you will bypass all the security features of **Linux**.

Ubuntu -- Not Linux. Don't mislead our newer users.

---

