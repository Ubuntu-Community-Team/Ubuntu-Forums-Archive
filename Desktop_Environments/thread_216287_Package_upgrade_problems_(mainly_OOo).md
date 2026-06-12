---
title: "Package upgrade problems (mainly OOo)"
date: 2006-07-15
forum: Desktop Environments
---

### Post by openback on 2006-07-15
Right now I am unable to upgrade any of my packages. I am greeted with this error whenever I try, even if I select upgradable packages *other* than OpenOffice

```


E: /var/cache/apt/archives/openoffice.org-l10n-en-us_2.0.2-2ubuntu12.1_all.deb: unable to create `./usr/lib/openoffice/program/resource/abp680en-US.res'
E: /var/cache/apt/archives/ttf-opensymbol_2.0.2-2ubuntu12.1_all.deb: unable to create `./usr/share/fonts/truetype/openoffice/opens___.ttf'
E: /var/cache/apt/archives/openoffice.org-core_2.0.2-2ubuntu12.1_i386.deb: unable to create `./usr/lib/openoffice/program/libflash680li.so'
E: /var/cache/apt/archives/openoffice.org-common_2.0.2-2ubuntu12.1_all.deb: unable to create `./usr/lib/openoffice/program/java-set-classpath'
E: /var/cache/apt/archives/python-uno_2.0.2-2ubuntu12.1_i386.deb: subprocess new pre-removal script returned error exit status 123
E: /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb: unable to create `./usr/share/man/de/man1/login.1.gz'


```

I have no idea would could be causing this error. I know that the drives are not full for one thing. Any ideas?

---

### Post by rubso on 2006-07-15
maybe it needs a "sudo" first?

---

### Post by openback on 2006-07-15
No, I always run synaptic or apt-get through sudo (or gksudo).

---

### Post by openback on 2006-07-17
Any help? I'm unable to use apt-get to install or update anything because of this error.

---

