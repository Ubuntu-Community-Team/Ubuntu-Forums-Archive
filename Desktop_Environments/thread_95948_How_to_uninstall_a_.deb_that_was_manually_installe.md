---
title: "How to uninstall a .deb that was manually installed? (Solved)"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Darrin on 2005-11-27
If I installed something that was not installed using add applications, how do I unisntall it? If some one has a link that explains this please post. 
Thanks

---

### Post by aysiu on 2005-11-27
How *did* you install it? From source? From a .deb? From a .rpm?

---

### Post by Darrin on 2005-11-27
Installed from a .deb.

---

### Post by lothar_m on 2005-11-27
just use synaptic.

---

### Post by invalid on 2005-11-27
[QUOTE=Darrin]Installed from a .deb.[/QUOTE]
If you installed from a .deb file, it should now be included in the installed package listing. You can use synaptic to search and remove it.

Cheers,
Cb

---

### Post by Xian on 2005-11-27
If you install a deb package manually with the dpkg command it will be recognized by apt and is automagically included in the package management system. This means that it can be removed by the tradition means. However, it might not be able to be reinstalled in apt or synaptic since those programs depend on the source of the .deb file being available. There are methods by which you can do this locally, but it really is too much trouble if it is only a few files that we are talking about.

---

### Post by Darrin on 2005-11-27
[QUOTE=invalid]If you installed from a .deb file, it should now be included in the installed package listing. You can use synaptic to search and remove it.

Cheers,
Cb[/QUOTE]
Wow. Did not know that. :) Thats great!

---

