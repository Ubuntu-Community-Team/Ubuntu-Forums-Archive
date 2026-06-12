---
title: "Business-class rollout of Desktop (possibly-virtual)"
date: 2012-07-06
forum: Desktop Environments
---

### Post by LHammonds on 2012-07-06
My company has 200+ Windows XP machines and some newer PCs are Windows 7.

I am looking for a desktop solution that is easy to maintain and keep updated.

Our main applications are delivered via Citrix and many apps/sites require Internet Explorer (yes, it irks me to no end) and Java (JRE).  I have seen some articles that show how to install IE 5.0, 5.5, and 6.0 on Linux (version 7.0 and 8.0 possible with potential problems)

Using Wyse terminals is one possible solution but that simply shifts costs from the PC to the server and opens more potential headaches.

Replacing Windows with Linux can reduce the cost of licensing but still requires maintenance and customizing access to application data for people that float around from PC to PC (email, Citrix, printers, etc.).

I was thinking about this (let me know if this can be done...or has been done)...a bare-bones install of a Linux OS (no GUI) which acts like an ESXi server which then fires up a virtual desktop image.  This virtual machine would be what the end-user interacts with.  As part of a maintenance process, the background process on this host OS then checks the main repository/distribution share for an updated desktop image.  If one is found, it then streams it to the machine in the background to a staging area while the user continues to use the desktop VM.  The next time the machine is rebooted, the old desktop image is moved into an archive/deletion area and the new image is then moved from the staging area to the production area and is then started up.

Of course, this means the desktop image will need to be configured in such a way that user data is stored in an unchanging area of the machine or kept on a network share or in sync with both.  This process would allow the IT department to keep the image updated with security patches and application updates...all done on a single image...one time.

Any thoughts about this process?  Is it too complex for the tools available?  Are there better ways to manage desktops?  Is anyone doing something similar to this?

Thanks,
LHammonds

---

### Post by LHammonds on 2012-07-09
Anyone?

---

