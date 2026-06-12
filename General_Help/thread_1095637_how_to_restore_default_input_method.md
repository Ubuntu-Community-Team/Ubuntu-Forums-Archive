---
title: "how to restore default input method"
date: 2009-03-13
forum: General Help
---

### Post by beemzet on 2009-03-13
Hi guys, I used the following code to set SCIM as a default input method, but I want to restore UBUNTU's own default input method.
```

im-switch -z en_US -s scim
```

I'm using 9.04 latest release to date. Please give me some instructions.
Thank you

---

### Post by phaid on 2009-03-14
The -a option resets it back to the system default

I believe the syntax is
```
im-switch -a
```

---

### Post by beemzet on 2009-03-14
Thank you phaid, but I guess it is not working.
Take a look at the output:
```
No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.

```

---

