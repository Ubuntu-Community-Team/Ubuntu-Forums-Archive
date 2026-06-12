---
title: "How to share installed applications?"
date: 2009-02-06
forum: General Help
---

### Post by UranUtan on 2009-02-06
Hi,

Using Ubuntu 8.10 x32.

Is it possible for User B to launch a program installed by User A?

It seems like it is possible. When I installed VirtualBox, it is visible under Applications / System Tools menu for all users. Same thing for Open Office 3.0. However, when I installed a Windows game via Wine, the shortcut to start the game is placed on the desktop of User A. When logged in under user B, I don;t see this shortcut.

I assume this is by design. Is there anyway to make an installed program shareable by all users?

Thanks in advance.

---

### Post by mb_webguy on 2009-02-06
As long as it is installed to the /usr or /opt directories, then yes.  If it is installed to the user's home directory somewhere (which is rare), then probably not.

If you don't see a launcher in the menu for an application, just right-click the menu, select Edit Menus, and add a launcher for the application.

---

### Post by UranUtan on 2009-02-06
> **mb_webguy said:**
> As long as it is installed to the /usr or /opt directories, then yes.  If it is installed to the user's home directory somewhere (which is rare), then probably not.

If you don't see a launcher in the menu for an application, just right-click the menu, select Edit Menus, and add a launcher for the application.

I am afraid that I may deal with the "rare" case. The program I want to share is located at:
/home/userA/.wine/dosdevices/c:/Program Files/Bejeweled 2 Deluxe

---

### Post by theozzlives on 2009-02-06
Yeah Windows apps go in your /home directory, you'll have to install it for user B

---

