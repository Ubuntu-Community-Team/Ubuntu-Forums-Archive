---
title: "how do I find out what the system named of my mouse, possible MMB fix"
date: 2009-01-20
forum: General Help
---

### Post by Bubs on 2009-01-20
bugs.launchpad.net/ubuntu/+bug/309559

I want to try the fix mentioned in this launchpad report but I don't know how to find the name of my mouse.  The report says use "lshal" but I ran that in terminal and it found 101 devices.  and another problem is that I have a wireless logitech keyboard along with a logitech wireless mouse so I don't know which is which.

---

### Post by dcstar on 2009-01-20
> **Bubs said:**
> bugs.launchpad.net/ubuntu/+bug/309559

I want to try the fix mentioned in this launchpad report but I don't know how to find the name of my mouse.  The report says use "lshal" but I ran that in terminal and it found 101 devices.  and another problem is that I have a wireless logitech keyboard along with a logitech wireless mouse so I don't know which is which.

```
sudo lshal | grep [Mm]ouse
```

---

