---
title: "zip drive not mountable volume"
date: 2005-12-28
forum: General Help
---

### Post by chocolatetoothpaste on 2005-12-28
When I out in a zip disk and try to access it an error pops up which says "Error: given UDI is not a mountable volume".  Any ideas?  I don't know what this means, much less how to fix it.

---

### Post by hajk on 2005-12-29
How is the zip-drive connected to your computer? 

Have you checked the messages in /var/log/syslog when you connect the zip-drive and switch it on? You can do that in a terminal window by using the command "sudo tail -f /var/log/syslog". That should tell you whether it is recognized by the kernel, and you can take it from there. You might post that output here if you need any more assistance.

---

