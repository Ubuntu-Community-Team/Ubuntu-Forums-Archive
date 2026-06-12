---
title: "Dell X1 booting single-user, unmapped keys in &quot;Recovery Menu&quot;"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lylex on 2008-11-03
Hello all:

On my Dell X1 running Ubuntu 8.04, I am having problems booting into single-user mode via Grub.

I correctly append a "single" to the Grub command line, then get taken to the "Recovery Menu" and presented with "resume", "dpkg", "root", etc.  But my arrow keys, tab key, etc do not seem to be mapped correctly and only echo escape sequences on the screen.

If I boot Ubuntu, then do "telinit 1", I arrive at the same "Recovery Menu", but my keys are mapped, and I can get to a single-user command-line prompt.

Any advice is greatly appreciated, and thank you in advance.

....Lyle

---

### Post by lylex on 2008-11-05
Anybody??

Thanks...Lyle

---

### Post by Anencephalic on 2009-01-26
If I edit the kernel line in grub to boot up in single user mode by just appending "single" to the end of the existing line, then I cannot use the up and down arrows to select items in the recovery menu.  This is a very frustrating experience as you no doubt know.  However, if I remove the "ro" and "quiet" parameters at the same time, then the arrow keys work.

---

### Post by superm1 on 2009-01-27
Usually the problem is you are leaving the word "splash" in.  usplash appears to conflict with the curses based menu.

---

