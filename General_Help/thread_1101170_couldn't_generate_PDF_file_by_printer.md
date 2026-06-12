---
title: "couldn't generate PDF file by printer"
date: 2009-03-20
forum: General Help
---

### Post by x-dongzi on 2009-03-20
:(
I installed cups-pdf, and I could select the printer PDF to print files.
File -> Print -> PDF
And I could see the print message in the /var/log/messages file.
=========the Log============
Mar 20 13:51:11 dong-laptop kernel: [10654.800692] audit(1237528271.061:11): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/mnt/F/dong/PDF/456.pdf" pid=2083 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
============================

However, I couldn't see anything on the location /mnt/F/dong/PDF
It seems that no file was generated.
But I didn't see any error messages in /var/log/messages.

Does anybody know why?
Thanks.

---

### Post by kaibob on 2009-03-20
Did you create the directory PDF in your home directory? You have to do this manually and it has to be capitalized.

---

