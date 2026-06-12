---
title: "How to change the openoffice 2.0.3 user interface?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2006-07-14
Hi. I've just installed openoffice 2.0.3 tarballs and everything is working fine, unless for one thing: I can't configure it to use the brazilian portuguese user interface. 

Does anyone know where could I obtain it?

---

### Post by mssever on 2006-07-14
You probably need the package openoffice.org-l10n-pt-br.
```
sudo aptitude update
sudo aptitude install openoffice.org-l10n-pt-br
```

Note that it would be much easier to install Open Office using Synaptic or aptitude, than from a tarball. Plus, upgrades will be much easier.

---

### Post by Marcos.Rufino on 2006-07-14
> **mssever said:**
> You probably need the package openoffice.org-l10n-pt-br.
```
sudo aptitude update
sudo aptitude install openoffice.org-l10n-pt-br
```

Note that it would be much easier to install Open Office using Synaptic or aptitude, than from a tarball. Plus, upgrades will be much easier.

Thanks mssever but maybe you missed that I installed openoffice 2.0.3. It is not in any repo yet and there's no way to install it through synaptic. I've already installed openoffice.org-l10n-pt-br but it doesn't work because it is  not due to 2.0.3 but the previous version.

So I think all I need is a version of openoffice.org-l10n-pt-br tailored to 2.0.3. But I don't have the slightest idea of how to get it.

---

