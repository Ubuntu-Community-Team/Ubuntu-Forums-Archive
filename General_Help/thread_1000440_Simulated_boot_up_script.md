---
title: "Simulated boot up script?"
date: 2008-12-02
forum: General Help
---

### Post by Forgott3n on 2008-12-02
Hello,

We're making a film involving a someone hacking on a linux system. It can be completely fictional, like, Hollywood fictional.

Since I can't really find a script that runs out bogus hex scrolling values or something (we're going to use cmatrix for a bit) I'm asking if someone has a script that essentially looks like a normal linux boot?

Thanks!

---

### Post by jpkotta on 2008-12-04
Why can't you just have a booting Linux system?  I doubt someone went through the trouble because if they wanted to see what it looks like they can just reboot.  You can turn off all the fancy framebuffer stuff in Ubuntu by editing /boot/grub/menu.lst and getting rid of all the "quiet splash" options.

---

