---
title: "Installing for X11"
date: 2005-12-06
forum: Desktop Environments
---

### Post by vav on 2005-12-06
I wanted to install magic 7.3 (An Electronics Design Automation tool) on my breezy. It is available as source tarball. When I ran it's configuration script, it finds X11 libraries but not X11 headers. I assume here that it is looking for the X11 source headers.

Can I find these headers somewhere? I have libx-dev installed but couldnt find an explicit X11 source package like the kernel source packages.

Any workarounds?

Thanks,
--Vaibhav

---

### Post by kairu0 on 2005-12-06
Try "libx11-dev."

---

### Post by vav on 2005-12-06
Sorry I meant I had libx11-dev and xlibs-dev installed.

I apologize for the typo.
--Vaibhav

---

### Post by vav on 2005-12-07
Turns out I had to force the installer to use the proper x headers - it stubbornly kept looking in the wrong places.

--Vav

---

