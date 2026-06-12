---
title: "GDEBI, lost capacity to upgrade"
date: 2006-07-07
forum: Desktop Environments
---

### Post by ffi on 2006-07-07
I did a reinstall og Ubuntu, previously when clicking on a .deb of a package I had already installed gdebi used to upgrade but now it mentions the package conflicts with the already installed package and doesn't upgrade.

How to fix this?

---

### Post by Anduu on 2006-07-07
Need a little more info...like the exact error it gives you.

My initial suspision is that the new deb you are trying to install requires versions of certain files that UBuntu does not have.

I once tried to install a package which required a higher version of libc6 than what is available to Ubuntu thus I could/will not be able to install that deb.

---

### Post by lamego on 2006-07-07
That means that .deb package you are trying to install was packaged for your old version and not for Dapper. That is way its reporting version conflicts.

---

### Post by ffi on 2006-07-08
> **Anduu said:**
> Need a little more info...like the exact error it gives you.

My initial suspision is that the new deb you are trying to install requires versions of certain files that UBuntu does not have.

I once tried to install a package which required a higher version of libc6 than what is available to Ubuntu thus I could/will not be able to install that deb.

*error: Conflicts with the installed package 'opera'* is the exact message but I have upgraded opera dozens of times like this, upgrading one weekly to the next.

---

### Post by Anduu on 2006-07-08
Try uninstalling the old version of Opera first.

---

### Post by ffi on 2006-07-08
> **Anduu said:**
> Try uninstalling the old version of Opera first.

This works but before I could just install the new one and upgrade.

---

### Post by ffi on 2006-07-10
No one?

---

