---
title: "nvidia multi monitors"
date: 2011-08-04
forum: Desktop Environments
---

### Post by bradpurvis on 2011-08-04
i have a multi monitor set up using the nvidia x server settings. when i maximize a window it goes across both monitors and makes it hard to do anything. Is there a way around this?

---

### Post by bradpurvis on 2011-08-04
also my right monitor is higher than the left but the nvidia software won't let me adjust its height

---

### Post by realzippy on 2011-08-04
change in /etc/X11/xorg.conf

Option "NoTwinViewXineramaInfo" "False"
to
Option "NoTwinViewXineramaInfo" "True"

---

