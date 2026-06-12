---
title: "Disable indexation in Jaunty?"
date: 2009-06-14
forum: General Help
---

### Post by dementic on 2009-06-14
Hello!

Is there file indexation in Ubuntu 9.04 or other activity that record traces of used or browsed files?

Is there a way to disable them?

Thank you

---

### Post by Legace on 2009-06-14
> **dementic said:**
> Hello!

Is there file indexation in Ubuntu 9.04 or other activity that record traces of used or browsed files?

Is there a way to disable them?

Thank you

Do you mean "recent documents" of the Places menu?
If so, then type the following in Teminal:

```
rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
chmod 400 ~/.recently-used.xbel
```

---

### Post by dementic on 2009-06-14
Thank you, I already deleted disabled recent documents. I meant indexation for file search, like windows does and ubuntu 7.10 I think

---

### Post by mike555 on 2009-06-14
You can just turn off the service , in system, admin., services........

---

### Post by dementic on 2009-06-14
There is no service for indexation

---

### Post by mike555 on 2009-06-18
On Hardy it's under "System" , Preferences , sessions , startup programs tab ...........

---

