---
title: "Anjuta Hangs"
date: 2005-04-02
forum: Desktop Environments
---

### Post by Reb on 2005-04-02
Exactly like here:
[http://www.ubuntuforums.org/showthread.php?t=17809&highlight=anjuta](http://www.ubuntuforums.org/showthread.php?t=17809&highlight=anjuta)
A stack trace:```
stat("/usr/share/locale-langpack/en_GB/LC_MESSAGES/anjuta.mo", 0x7fbffff630) = -1 ENOENT (No such file or directory)
getpid()                                = 31242
rt_sigaction(SIGINT, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2a9a79a820) = 31245
wait4(31245, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 31245
rt_sigaction(SIGINT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
rt_sigreturn(0x74b2f0)                  = 0
open("/tmp/anjuta_0.31242", O_RDONLY)   = 16
fstat(16, {st_mode=S_IFREG|0644, st_size=3463, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a9b84e000
read(16, "pyorbit-2             PyORBit - "..., 4096) = 3463
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
write(3, "\236\21\3\0002\0\0\4\240\0\0\0\236\24\31\0002\0\0\4\1\0"..., 5344) = 5344
write(3, " \21\2\0\0\0\0\0", 8)         = 8
write(3, "+\21\1\0", 4)                 = 4
read(3, "\1\2\v\1\0\0\0\0\4\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\224\322"..., 32) = 32
futex(0x2a9a1465c0, FUTEX_WAIT, 2, NULL
```

---

### Post by Reb on 2005-04-02
[http://sourceforge.net/mailarchive/forum.php?thread_id=6859564&forum_id=7093](http://sourceforge.net/mailarchive/forum.php?thread_id=6859564&forum_id=7093)
A known bug in 1.2.2-6.

---

