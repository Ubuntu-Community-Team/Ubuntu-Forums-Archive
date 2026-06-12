---
title: "Hi Brand New nwn on 8.04 not wking removed lib"
date: 2008-07-28
forum: Gaming &amp; Leisure
---

### Post by a11b1ts0n on 2008-07-28
Hi,

I am brand new to linux, have been working with windows for about 10 years and so far am really happy with the change. I am having some trouble with nwn though, i have a geforce go 4 video card, with hardy 8.04 and I am getting the failed to initialize graphics segmentation fault error. I have dl the patch, removed the lib dir and the reference in the nwn script. I also am using the glx driver for the nvidia card. Any help would appreciate it very much! Thanks!

results from strace:
read(3, 0xe0b7ad4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
close(3)                                = 0
munmap(0xb7f42000, 20988)               = 0
rt_sigaction(SIGSEGV, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGBUS, NULL, {0xb7cf7010, [], 0}, 8) = 0
rt_sigaction(SIGBUS, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGFPE, NULL, {0xb7cf7010, [], 0}, 8) = 0
rt_sigaction(SIGFPE, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {0xb7cf7010, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
tgkill(21540, 21540, SIGSEGV)           = 0
sigreturn()                             = ? (mask now [])
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 21540 detached
chris@chris-laptop:~/nwn$

---

