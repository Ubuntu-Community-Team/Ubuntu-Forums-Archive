---
title: "something really odd with SCIM"
date: 2006-11-29
forum: Desktop Environments
---

### Post by yuyueyuyue on 2006-11-29
I installed SCIM, and im-switch. (locale: en_US)
And SCIM is always running in the background, with the tray icon.

but everytime I open a Synaptic Package Manager, a new SCIM session will start. Thus there could be more than one tray icon in the taskbar.

I cannot tell why. Can somebody help?

Thanks in advance!

---

### Post by twjo on 2007-01-04
I think this is not an odd situation for SCIM.

You will need SU (sudo/gksu) to launch Synaptic, and since its a different userspace, a different SCIM will need to be launch. You can try other apps that needs SU, it will be the same situation where a new SCIM will be launch.

---

