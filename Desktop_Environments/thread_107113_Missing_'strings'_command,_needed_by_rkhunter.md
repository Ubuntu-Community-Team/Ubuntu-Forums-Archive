---
title: "Missing 'strings' command, needed by rkhunter?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by gmc on 2005-12-22
Greetings All,

I recently installed rkhunter (RootKit Hunter).  Each day I receive and email from rkhunter complaining that the program 'strings' is missing from my system. I checked with [www.debian.org](www.debian.org) and discovered that the 'strings' command should be included with the binutils package. When I check my installed packages, I have binutils-static 2.16.1-2 installed but there is no 'strings' command in it. Has it been moved to another package? If so where?

G.

---

### Post by heimo on 2005-12-22
Try installing binutils package (not same as binutils-static).

---

### Post by gmc on 2005-12-22
[QUOTE=heimo]Try installing binutils package (not same as binutils-static).[/QUOTE]

Bingo! That's where is was. I thought that binutils-static was the same as binutils only the programs were statically linked. Weird that binutils wasn't installed by defaults as it is in Debian.

Thanks
G.

---

