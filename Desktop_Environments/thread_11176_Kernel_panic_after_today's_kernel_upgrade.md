---
title: "Kernel panic after today's kernel upgrade"
date: 2005-01-14
forum: Desktop Environments
---

### Post by acidmax on 2005-01-14
Hello

Just upgraded my kernel to linux-image-2.6.8.1-4-386_2.6.8.1-16.8_i386 ([USN-60-0](http://www.ubuntulinux.org/support/documentation/usn/usn-60-0)).
After reboot I've got two kernel panics about "Unable to handle kernel NULL pointer dereference at virtual address ..." (unfortunately I don't have screenshots). On the third boot it worked by itself. I was wondering did someone other experienced the same behaviour?!

---

### Post by hardcandy on 2005-01-14
What does "uname -r"  tell you? Just making sure you are using the new kernel.

---

### Post by acidmax on 2005-01-14
acidmax@catalina:~ $ uname -r
2.6.8.1-4-386

The updated version did not get listed as new kernel in my GRUB menu, it just replaced the other 2.6.8.1-4. I have two machines running Ubuntu. One updates from the other, and encountered no problems.

---

