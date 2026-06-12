---
title: "xfce places plugin with nautilus"
date: 2012-06-03
forum: Desktop Environments
---

### Post by tivatranquio on 2012-06-03
Is there a way to makes this plugin works with nautilus??

I have founded something like making "/usr/bin/thunar" a symlink to nautilus, but I don't like this solution..

---

### Post by brainwash on 2012-06-03
> **tivatranquio said:**
> I have founded something like making "/usr/bin/thunar" a symlink to nautilus, but I don't like this solution..

Symlinking would be the easiest solution. How about editing the particular source file (to force the use of *exo_execute_preferred_application*) and compiling the plugin from source? Is that a solution you would like?

---

