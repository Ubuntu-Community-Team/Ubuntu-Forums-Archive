---
title: "Missing desktop icons"
date: 2019-01-05
forum: Desktop Environments
---

### Post by horrido on 2019-01-05
First, let me say I'm new to Linux.

Second, I recently purchased a VPS from OVH and I installed Ubuntu Server 18.04.1 LTS 64-bit.

Then, I installed Xfce4 using this command:

sudo apt install xfce4 xfce4-goodies

However, upon completion, I noticed that nearly all of the application icons were missing! They're missing in the File Manager. They're missing in the top-level Applications menu (oddly, they're not missing in the submenus). They're missing in the dock, except for File Manager and "Minimize all open windows and show the desktop".

Interestingly, Trash, File System, and Home on the desktop show their icons.

How can I recover the missing desktop icons?

---

### Post by horrido on 2019-01-06
I found the fix. I downgraded to Ubuntu 16.04 and now everything works fine. Apparently, Ubuntu 18.04 is a little broken in this respect. If anybody cares to fix this, go ahead, but I no longer care.

---

