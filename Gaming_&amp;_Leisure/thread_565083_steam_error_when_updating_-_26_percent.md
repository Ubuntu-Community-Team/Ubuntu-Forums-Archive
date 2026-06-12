---
title: "steam error when updating - 26 percent"
date: 2007-10-01
forum: Gaming &amp; Leisure
---

### Post by ajfunk on 2007-10-01
Im sure the answer has been posted before, but i've been searching and searching the boards and can't find it. I got Steam installed through wine and when i try to update it gets too 26 percent, then says "a copy of steam is already running". Anybody have the command I need to run to fix this issue? I've tried the steamtmp.exe selfupdate 14 command, but to no avail sadly.

---

### Post by DoktorSeven on 2007-10-01
Renice it, at 26% the updater relaunches itself but Wine doesn't shut it down fast enough so it thinks it's running twice.

nice -n 19 Steam.exe

---

### Post by ajfunk on 2007-10-01
can you post the complete string? that command doesnt work as is.

---

### Post by DoktorSeven on 2007-10-01
I forgot the wine part.  Oops.

nice -n 19 wine Steam.exe

---

