---
title: "Connect to internet in terminal"
date: 2009-03-31
forum: General Help
---

### Post by RedSingularity on 2009-03-31
How can i connect to my wireless network in terminal mode?  I am installing the new Nvidia drivers.  To do so i cant have the X server running hence terminal mode, and during install it needs to access the Internet which is why i need a connection.

---

### Post by 3rdalbum on 2009-04-01
I'm not sure of how to connect to wireless from a terminal, but the Nvidia driver installer can just compile a new kernel interface while-you-wait rather than download a precompiled one. It will only take about 5 seconds to compile.

You will need the "-headers" package for the Linux kernel that you are currently running. You can get it from Synaptic Package Manager. When the Nvidia driver asks you if you want to download a precompiled kernel interface, just go to "no" and it will offer to compile it for you.

---

### Post by RedSingularity on 2009-04-01
Great.  I got it working.  Thanks!

---

