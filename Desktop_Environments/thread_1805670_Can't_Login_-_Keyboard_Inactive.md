---
title: "Can't Login - Keyboard Inactive"
date: 2011-07-16
forum: Desktop Environments
---

### Post by ldeathrg on 2011-07-16
I recently upgraded to Ubuntu 11.04.  Login worked fine at first. After a recent update, I can no longer login.  The Keyboard is inactive on the home screen.  Mouse is active and I can enter through other non-admin accounts with no password required for their login.  Keyboard works fine once I can get past the login. 
Doesn't work on normal, classic or safe mode.  Keyboard driver (system-wide)set to Dell Inspiron 6xxx/8xxx.

Help please.

Dell Inspiron 8600 laptop
Ubuntu 11.04

---

### Post by Krytarik on 2011-07-16
When you are at the login screen, click on the Accessibility icon on the bottom panel, usually a man in a ring.

In the dialog that comes up then, make sure the very last option, "Slow Keys", is disabled.

Alternatively, just run this command:
```
sudo -u gdm gconftool-2 /desktop/gnome/accessibility/keyboard/slowkeys_enable --type bool --set false
```
Greetings.

---

### Post by ldeathrg on 2011-07-17
Thanks, disabling the 'Slow Keys' option on the accessibility dialog fixed the issue.  I appreciate your quick response. What a great support community.

---

