---
title: "KMail exists but no menu?"
date: 2005-08-19
forum: Desktop Environments
---

### Post by tilleyrw on 2005-08-19
Performing a "dpkg -l | grep kmail" shows that kmail is indeed loaded on my Kubuntu 5.04 system.  But there is a noticeable discrepancy -- "kmail" does not appear in the Internet menu.

To add it to my toolbar necessitated creating an application icon, linking it to kmail, then dragging it onto the toolbar.  Why does it not appear in the Internet folder after install?

Thanks, Bob

---

### Post by Sarojin on 2005-08-19
I noticed the same thing.

---

### Post by apokryphos on 2005-08-19
Kubuntu chose to stick with the Kontact integration; thus you'll also miss several other kdepim components in the menus. All other KDE PIM stuff integrates into Kontact (the personal information manager itself), which includes KMail. Kontact appears in the menus.

This poses questions since "PIM" or "Personal Information Manager" doesn't always scream Mail, News, Feeds etc, and indeed the whole menu style could be up for debate.

---

