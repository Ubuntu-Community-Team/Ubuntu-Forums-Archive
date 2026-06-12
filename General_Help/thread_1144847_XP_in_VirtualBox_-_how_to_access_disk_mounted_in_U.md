---
title: "XP in VirtualBox - how to access disk mounted in Ubuntu?"
date: 2009-05-01
forum: General Help
---

### Post by Robert Leithe on 2009-05-01
I'm running Jaunty, and Virtual Box OSE. In VB I have an WinXP installation running. My laptop has two internal drives.
(How) can I access files on one of these drives from my XP installation?

Sincerely
Robert

---

### Post by manuelb on 2009-05-01
Have you tried to share them via a Samba share?

---

### Post by andrew.46 on 2009-05-01
Hi Robert,

> **Robert Leithe said:**
> I'm running Jaunty, and Virtual Box OSE. In VB I have an WinXP installation running. My laptop has two internal drives.
(How) can I access files on one of these drives from my XP installation?

If you have installed the guest additions set yourself a shared folder. Then within that folder place a link to the drive on your host that you wish the guest to access. This works for external drives and usb devices as well.

Andrew

---

### Post by disabledaccount01 on 2009-05-01
Message removed by author.

---

### Post by Robert Leithe on 2009-05-01
A Samba share works fine. Thank you! :)

---

