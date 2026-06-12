---
title: "Apt error"
date: 2006-01-11
forum: Desktop Environments
---

### Post by joselin on 2006-01-11
Hi,

When i tryed to install the package libgnutls11-dev i received the following:

```

libgnutls11-dev:
  Depends: libgnutls11 (=1.0.16-13.1) but 1.0.16-13.1ubuntu1 is to be installed

```

The package required is instaled and i don't know why installation fails.

Anybody can help me.

Regards,
Jose

---

### Post by newuser111 on 2006-01-11
the problem is that there is a version difference between the installed version and the version required by the application

---

### Post by Thirsteh on 2006-01-11
Apparently you don't have the Ubuntu version of libgnutls11? That's the only difference between those version numbers.. Try reinstalling it with Synaptic.

---

### Post by joselin on 2006-01-11
I have the 1.0.16-13.1ubuntu1 version installed. And is the only version that appears.

---

### Post by joselin on 2006-01-11
I find out the solution. There is an option in synaptic called package / force version... i had to downgrade that lib... after that i could install libgnutls-dev.

Thanks.

---

