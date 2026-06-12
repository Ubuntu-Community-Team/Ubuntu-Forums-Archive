---
title: "The system has no more ptys."
date: 2009-06-18
forum: General Help
---

### Post by ReyJavikVI on 2009-06-18
I'm building a [Linux From Scratch]("http://www.linuxfromscratch.org") system using Ubuntu 9.04 as the host. [Section 6.11]("http://www.linuxfromscratch.org/lfs/view/stable/chapter06/binutils.html") of the book tells me to run the command "expect -c "spawn ls". I did, and the expected error message "The system has no more ptys. Ask your system administrator to create more." appeared. How do I fix this?

---

### Post by geirha on 2009-06-18
Have you mounted /dev and /dev/pts as explained here?

[http://www.linuxfromscratch.org/lfs/view/stable/chapter06/kernfs.html#ch-system-bindmount](http://www.linuxfromscratch.org/lfs/view/stable/chapter06/kernfs.html#ch-system-bindmount)

---

### Post by ReyJavikVI on 2009-06-18
I was sure I had done that, but I did it anyway and tried again and worked. I think I had forgot to run those as root.

Thanks.

---

