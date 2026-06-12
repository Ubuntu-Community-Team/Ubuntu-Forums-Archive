---
title: "try copy home directory to windows disk."
date: 2009-05-04
forum: General Help
---

### Post by JohnPta on 2009-05-04
I try to copy my "home" directory to my windows disk. Under normal conditions it tells me "No permission" so I went in to terminal logged in as root user and loaded "gksudo nautilus" and tried the same again and still I get the message "you do not have the permission".

How can I copy my "home" directory?? in order to save my setup before I will upgrade to 9.04??

---

### Post by akoskm on 2009-05-04
> **JohnPta said:**
> I try to copy my "home" directory to my windows disk. Under normal conditions it tells me "No permission" so I went in to terminal logged in as root user and loaded "gksudo nautilus" and tried the same again and still I get the message "you do not have the permission".

How can I copy my "home" directory?? in order to save my setup before I will upgrade to 9.04??

You are logged in as root, so I think that the problem caused by mounting the partition without rw permissions. Post here the output of
```

cat /etc/fstab

```command
.

---

### Post by aaronp on 2009-05-04
> **JohnPta said:**
> I try to copy my "home" directory to my windows disk. Under normal conditions it tells me "No permission" so I went in to terminal logged in as root user and loaded "gksudo nautilus" and tried the same again and still I get the message "you do not have the permission".

How can I copy my "home" directory?? in order to save my setup before I will upgrade to 9.04??

There should be no need to 'login as root'.
If you do gksudo then you will enter your password as yourself but also have root privileges for nautilus. This should do it for you...

---

