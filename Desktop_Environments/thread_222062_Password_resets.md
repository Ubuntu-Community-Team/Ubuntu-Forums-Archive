---
title: "Password resets"
date: 2006-07-24
forum: Desktop Environments
---

### Post by etank on 2006-07-24
Is there a tool or setting that will enforce password complexity/changes/expiration for Ubuntu. I have seen something in SuSE but I don't recall what it was. I want a reminder to change my password every 30 days or so. I think that NIS or NIS+ will do it but this is on a local system not a network.

Thanks.

---

### Post by mystdragon on 2006-07-24
for changes/expiration, try:
sudo passwd -x 30 -w 5 <username>

-x <days> is maximum time a password is considered valid; -w <days> is useful for providing a warning <days> days ahead of the password expiration.

You will have to do some searching on the subject, but I believe you can use crack to check for password complexity at the time of a password change.

---

