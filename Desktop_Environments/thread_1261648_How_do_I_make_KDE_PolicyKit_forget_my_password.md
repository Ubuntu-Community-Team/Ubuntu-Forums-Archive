---
title: "How do I make KDE PolicyKit forget my password?"
date: 2009-09-09
forum: Desktop Environments
---

### Post by Virtualboxbuntu on 2009-09-09
I am a very security-conscious person and I prefer to have KDE ask for my password before I do updates/install software/ etc. However I accidentally told it to remember my password for updates, how do I make it forget the password?

---

### Post by Raboch on 2009-09-09
System Settings -> Advanced -> PolicyKit Authorization -> org.freedesktop -> The PackageKit Project -> Update packages -> Under Explicit Authorizations click your authorization and then the Revoke button.
That should do it.

---

### Post by Virtualboxbuntu on 2009-09-09
Yes it did. Thank you.

---

