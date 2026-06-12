---
title: "where go output from .profile file on login"
date: 2008-02-12
forum: Dell  Ubuntu Support
---

### Post by Ralph Boland on 2008-02-12
If I put a "echo hello" command in my .profile file then I do not see the
output  "hello" when I log in (usually when my computer is started).
However, I need to see such output and any error messages when
I log in to track down a problem I am having.  

This output must be stored in a file somewhere
But where?

Thanks for any help provided.

Ralph Boland

---

### Post by neptho on 2008-02-14
If you're using X11, it runs X before your shell; you will only see it when you open a terminal.

If you wish to log things, consider using logger (part of syslog), or redirection.  "echo foo > myfile".

Reading up on your shell, and basic UNIX commands may be to your benefit.  Good luck!

---

