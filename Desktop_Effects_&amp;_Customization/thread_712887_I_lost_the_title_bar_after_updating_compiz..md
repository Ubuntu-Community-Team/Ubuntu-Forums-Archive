---
title: "I lost the title bar after updating compiz."
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by amazingjxq on 2008-03-02
I updated it in the update manager. After that i see the compiz-gnome is still the old version. When I double click on it, it shows this:
compiz-gnome:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
what the hell is this?
Can I uninstall these updates?

---

### Post by jeffus_il on 2008-03-02
Install the package "emerald".

---

### Post by amazingjxq on 2008-03-02
emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable

---

### Post by jeffus_il on 2008-03-02
Emerald installs here fine. Have a look at your repositories in Synaptic. Use Settings->Repositories. You may have to check universe or restricted and then hit the "reload" button.

---

