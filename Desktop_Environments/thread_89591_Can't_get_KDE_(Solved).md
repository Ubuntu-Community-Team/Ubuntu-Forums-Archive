---
title: "Can't get KDE (Solved)"
date: 2005-11-13
forum: Desktop Environments
---

### Post by jsmidt on 2005-11-13
I try ti intsall KDE and this is what my machine says:
```

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdesdk but it is not going to be installed

```

    What is the problem?

---

### Post by jsmidt on 2005-11-13
I fixed the problem, I discovered one package depended upon another until I found one installed that wasn't the right version.  I removed it, reinstalled the right version and like a domino effect it works :razz:

---

