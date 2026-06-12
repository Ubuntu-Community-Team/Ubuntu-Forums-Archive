---
title: "Open port below 1024 as normal user?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by apoth on 2005-09-29
How do I give permissions to a normal user to open up ports (I think it's below 1024)?

---

### Post by FLeiXiuS on 2005-09-29
You can't, it's impossible.

---

### Post by cwaldbieser on 2005-09-29
[QUOTE=apoth]How do I give permissions to a normal user to open up ports (I think it's below 1024)?[/QUOTE]
What is the reason you want to do that?  There may be a more traditional solution to your problem.

---

### Post by wmcbrine on 2005-09-30
You can't, but you can get a server process to drop root privileges after it acquires the port. Or, you can set up forwarding from a privileged port to a nonprivileged port. Of course you still need root access to do these things, but at least the server process doesn't have to run as root.

---

### Post by apoth on 2005-09-30
[QUOTE=cwaldbieser]What is the reason you want to do that?  There may be a more traditional solution to your problem.[/QUOTE]

I've been developing a program and have imported a third party library that seemingly requires opening a port below 1024. I haven't checked exactly which.

If I try doing it as root I suspect my IDE won't open up the software as it's saved against the user I've been writing it under. I'm sure it's not impossible, if not worth editing the kernel for.

---

### Post by cwaldbieser on 2005-09-30
[QUOTE=apoth]I've been developing a program and have imported a third party library that seemingly requires opening a port below 1024. I haven't checked exactly which.

If I try doing it as root I suspect my IDE won't open up the software as it's saved against the user I've been writing it under. I'm sure it's not impossible, if not worth editing the kernel for.[/QUOTE]
What does the library do (is there a web link we can read about it)?

---

### Post by apoth on 2005-10-01
Thanks for the continued interest.

It's called [escher](http://escher.sourceforge.net/), it's a java library to provide an equivalent to C/C++'s xlib. The particular class throwing the error was [Connection](http://escher.sourceforge.net/current/doc/index.html).

---

