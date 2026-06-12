---
title: "Querying package post-install scripts"
date: 2009-03-24
forum: General Help
---

### Post by dal553 on 2009-03-24
Is there a way to find the post-installation scripts that a package runs?

In the RPM world, I can do a rpm -q --scripts <pkg name> and it returns to me the scripts tied to that particular package.

Is there a dpkg equivalent?

Thanks.

---

### Post by iiska on 2009-05-18
You can extract dpkg's control scripts from the deb file with:

ar x package.deb control.tar.gz

Then extract control.tar.gz to access actual scripts:

tar zxf control.tar.gz

---

