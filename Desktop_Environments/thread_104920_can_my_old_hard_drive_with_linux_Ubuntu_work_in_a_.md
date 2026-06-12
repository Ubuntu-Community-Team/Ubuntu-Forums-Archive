---
title: "can my old hard drive with linux Ubuntu work in a new computer system"
date: 2005-12-17
forum: Desktop Environments
---

### Post by lignito on 2005-12-17
can my old hard drive with linux Ubuntu work in a new computer system?

---

### Post by schdefan on 2005-12-17
Yes it can. Be sure to have set the symbolic link of hotplug so that the newer hardware is found at boot time.
you can do that in a terminal as root with.
```
#update-rc.d hotplug defaults
```

schdefan

---

### Post by lignito on 2005-12-17
Thank you very much!! I will try it!

---

