---
title: "Openoffice 3.2 crash question"
date: 2010-07-07
forum: Desktop Environments
---

### Post by zong1 on 2010-07-07
Hi,
   OO write crashes today and now refuses to start.  strace gives:

```

mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb772e000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb772e8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xdef000, 8192, PROT_READ)     = 0
mprotect(0x805c000, 4096, PROT_READ)    = 0
mprotect(0xb50000, 4096, PROT_READ)     = 0
munmap(0xb772f000, 82887)               = 0
getpid()                                = 11176
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x93a7000
brk(0x93c8000)                          = 0x93c8000
getppid()                               = 11175
stat64("/home/s-loewenthal", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/ooffice", O_RDONLY)      = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x804f636, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], 0}, NULL, 8) = 0
read(10, "#!/bin/sh\n/usr/lib/openoffice/pr"..., 8192) = 52
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb772e938) = 11177
wait4(-1, 

```

I removed both write and calc and then reinstalled but same error is given.  Additionally, I deleted the user profile ~/.openoffice.org directory and let OO recreate it, but it still won't start.

# aptitude purge openoffice.org-writer openoffice.org-calc  && aptitude install  openoffice.org-writer openoffice.org-calc

Any ideas?

---

### Post by zong1 on 2010-07-12
I tried again to remove anything OpenOffice related, and still it won't work.  Abiword works fine.  Could someone offer me carrot - A pointer where I could start to debug this?

---

### Post by Hagar Delest on 2010-07-14
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun/Oracle version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by zong1 on 2010-07-14
Hi,

  As noted in my original post I did "delete ~/.openoffice.org directory and let OO recreate it,...".
Since then I have installed the packages from Sun, instead of the ones via Ubuntu, and it did not make any difference.

However, I ran OO as another user, and it works, which means that it is user configuration specific.  

Sadly, deleting the ~/.openoffice.org does not make any difference so its not this.  

Are there any other OO related files around other than ~/.openoffice.org ?

z

---

### Post by Hagar Delest on 2010-07-14
Sorry, had missed the profile reset.

Is there any special character in your username?
You could try to copy the working profile of the other user to your account (change the rights if needed).

---

### Post by zong1 on 2010-07-14
Nope. nothing special in the username.  It used to work before, until someone in HR sent me a horrible (I cannot define what horrible is) XL file to complete. It crashed while editing, and would never start afterwards.

I'll copy the file across.

---

