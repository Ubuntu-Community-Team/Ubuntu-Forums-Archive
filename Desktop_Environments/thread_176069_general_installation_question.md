---
title: "general installation question"
date: 2006-05-14
forum: Desktop Environments
---

### Post by whoa_551 on 2006-05-14
Is it okay in Ubuntu to install platform-independent source files to install a program or is it only advisable to use Ubuntu .deb packages?  For instance, if program XYZ v2.0 is in the repositories, and I want v3.0, but there is no .deb for it, can I install the source obtained from XYZ's website, or will that just create a dependency nightmare, leaving me with two broken apps, and possibly a broken system?

---

### Post by engla on 2006-05-14
[QUOTE=whoa_551]... or will that just create a dependency nightmare, leaving me with two broken apps, and possibly a broken system?[/QUOTE]
It could be anything in that range, depending on the quality of the source package and how you configure & install that package.

I woulnd't hesitate to try though if XYZ is an application, that is not a library or system-critical daemon/service.

---

### Post by Sef on 2006-05-14
> s it okay in Ubuntu to install platform-independent source files to install a program or is it only advisable to use Ubuntu .deb packages? For instance, if program XYZ v2.0 is in the repositories, and I want v3.0, but there is no .deb for it, can I install the source obtained from XYZ's website, or will that just create a dependency nightmare, leaving me with two broken apps, and possibly a broken system?

Anything can happen.  Usually you will get a notice what is missing and install that.  Of course it may need another dependcy and you can slide into dependency hell.

---

### Post by whoa_551 on 2006-05-14
If I get an error message saying "libxxx not found", can I install it and then be able to run the app, or do I then need to reinstall the app after installing libxxx?  Is there a situation where I would have to uninstall* then* reinstall the app to get it working after installing libxxx?  (are we getting confused yet?)

---

