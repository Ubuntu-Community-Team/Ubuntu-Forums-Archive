---
title: "restricted modules help"
date: 2006-09-18
forum: Desktop Environments
---

### Post by poncenby on 2006-09-18
here's what I did:

Removed (dpkg --purge) these packages:

restricted-modules-amd64-k8
nvidia-kernel-common
nvidia-glx

Installed nvidia blob from their site, version 8774 I think.
It works great.

but now when I try to install anything, in this example mysql-admin, apt-get complains about a few packages (including nvidia-kernel-common) depending on the restricted-modules package.

is there any way of making it so the restricted modules package isn't so critical.

thanks in advance

poncenby

---

### Post by Ramses de Norre on 2006-09-18
I think you might be able to change the dependencies in /var/lib/dpkg/status. But I'm not sure.. so make back ups ;)

---

