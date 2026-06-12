---
title: "GDM - Login problem"
date: 2012-03-09
forum: Desktop Environments
---

### Post by phanohanover on 2012-03-09
Hi there, I have an issue with an 11.04 installation.
It was setup for automatic login.
I recently added a user. I have changed the automatic login to normal login with user prompt. However, now when I get to login screen, it shows the 2 users and the "other" as well. But when I click on a user, it seems to choose it for half a second then it comes back to user prompt windowIt does not even get to asking for password.

If I change custom.conf in gmd to automatic-true, then it logs in ok.
Even there, I am unable to switch to the other user. It won't let me.

Anyone has an idea?

Stephane

---

### Post by pavi_elex on 2012-03-10
Try to set the password for user using
```
sudo passwd "username without quote"
```

---

