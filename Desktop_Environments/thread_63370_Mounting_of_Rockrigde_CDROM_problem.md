---
title: "Mounting of Rockrigde CDROM problem"
date: 2005-09-07
forum: Desktop Environments
---

### Post by ddubuntu on 2005-09-07
Hi all,

I have burned some CDs with K3B (default option, only Rockridge selected) but now when I mount the CDs, the international characters are replaced by square symbols.
In fstab, I use the utf8 and iocharset=8859-1 options.

David.

---

### Post by mlomker on 2005-09-07
What application to you see the characters in?  From the command prompt or a file explorer?  Try looking at the contents from /media/cdrom in a terminal prompt.

I'm thinking there is a language pack/localization problem but you'll want to figure out if it is at the Xfree level or the operating system level...try to narrow it down.

---

### Post by ddubuntu on 2005-09-08
Thanks, I have found the solution, it was a problem of locales.
I have run sudo dpkg-reconfigure locales, and addded the iso8859-1.
I think the system couldn't find the iso8859-1 charset (and convert to UTF8)

---

