---
title: "installed gcolor2 from Debian repositories"
date: 2006-03-15
forum: Desktop Environments
---

### Post by l_b on 2006-03-15
Hi,
Yesterday I installed gcolor2 from the debian repositories. I downloaded the package manually and used dpkg to install it. I used ignore to ignore warnings about missing packages.

But today I wanted to atp-get update and it didn't work. How do I resolve this error (without removing gcolor2 :) )

```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gcolor2: Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
           Depends: libglib2.0-0 (>= 2.8.5) but 2.8.3-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.10.2) but 1.10.1-0ubuntu1 is to be installed
           Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a  solution).

```

---

### Post by Xian on 2006-03-15
The only method is to upgrade to those higher versioned libraries.

---

### Post by l_b on 2006-03-15
Ok, thanks. And how do i do that?

---

