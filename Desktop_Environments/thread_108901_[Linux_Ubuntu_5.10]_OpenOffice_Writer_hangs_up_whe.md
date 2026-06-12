---
title: "[Linux Ubuntu 5.10] OpenOffice Writer hangs up when saving file"
date: 2005-12-27
forum: Desktop Environments
---

### Post by zimek on 2005-12-27
Hello.

I'm using OO 1.9.129 680 (Build:8825).
The system is Ubuntu Linux 5.10 with kernel 2.6.12-10-386 on Dell Latitude C610 laptop with 256 MB RAM and Intel Pentium III 1 GHz cpu.

When I open a .sxw document, modify it and try to save as .odt, OpenOffice Writer hangs up. It creates empty (0-bytes long) .odt file,
and does nothing more. When I attach do openoffice process by strace (unix diagnostic tool), I see that this process is waiting on futex() system call.

From futex man page:

"The futex() system call provides a method for a program to wait  for  a
value  at  a  given  address  to change, and a method to wake up anyone
waiting on a particular address (while the addresses for the same  mem-
ory in separate processes may not be equal, the kernel maps them inter-
nally so the same memory mapped in different locations will  correspond
for  futex()  calls).   It is typically used to implement the contended
case of a lock in shared memory, as described in futex(4)."

Anyone has this problem before ? Anyone knows what can be done for this to work correctly?

---

### Post by zimek on 2005-12-28
No one knows nothing about this problem?:( 

Maybe someone knows when new version of OpenOffice will be available in ubuntu ?:confused:

---

### Post by Sef on 2006-01-04
Have you tried uninstalling and reinstalling Openoffice?

---

