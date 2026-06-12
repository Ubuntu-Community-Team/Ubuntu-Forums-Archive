---
title: "No password needed for root terminal?"
date: 2005-02-15
forum: Desktop Environments
---

### Post by echinida on 2005-02-15
I attempted to change the root password from the first user password using the computer>system c onfiguration>users andgroups GUI but now I don't need any password to access a root terminal! Not very secure. I've repeated changing root password with sudo passwd root but I can still get a root terminal with no password. how can I fix this?

---

### Post by tim1 on 2005-02-15
If your user account has a good password the user sudo-approch is exactly (not 100% maybe, but very comparable) as safe as a root account with the same password.

However, if you want to change that you can access sudo, do this by edtiting the sudoers file with "visudo /etc/sudoers"

greets, tim

---

### Post by echinida on 2005-02-21
Thanks - but the problem now is that I (or anyone) have/has root access without a password. This is something I've done by trying to change the root password. I'd like to undo it.

---

