---
title: "Get power failure. After that file-manager hangs."
date: 2011-08-18
forum: Desktop Environments
---

### Post by Azyx on 2011-08-18
Hi.
For a few days ago i get a power-failure and my computers stop imediatly. After what the system periodically hangs and when i shutdown or reboot the file-manager not responding. i suspect some damage on the harddrive/filesystem. How do i fix it?

How to make a file-system check during boot?

/cheers

---

### Post by Azyx on 2011-11-12
> **Azyx said:**
> Hi.
For a few days ago i get a power-failure and my computers stop imediatly. After what the system periodically hangs and when i shutdown or reboot the file-manager not responding. i suspect some damage on the harddrive/filesystem. How do i fix it?

How to make a file-system check during boot?

/cheers

```
sudo touch /forcefsck

sudo reboot

```

---

