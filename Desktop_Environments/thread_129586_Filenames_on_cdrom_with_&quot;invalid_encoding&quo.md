---
title: "Filenames on cdrom with &quot;invalid encoding&quot;."
date: 2006-02-14
forum: Desktop Environments
---

### Post by nkbj on 2006-02-14
I have a few cdroms burned on Mandriva Linux (ISO-8859-1 character set) with filenames containing the characters æ, ø and å. The ISO images are made by "mkisofs -r" (no Joliet).

When I mount those cdroms on Breezy the filenames show up in the filebrowser and terminal with question marks in stead of the characters and followed by the message "invalid encoding". I have tried adding the options "iocharset=iso8859-1" and "iocharset=utf8" in /etc/fstab, but that didn't work.

Any ideas how to fix it?

Regards,
Niels Kristian

---

