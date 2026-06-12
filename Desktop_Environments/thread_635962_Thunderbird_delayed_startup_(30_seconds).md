---
title: "Thunderbird delayed startup (30 seconds)"
date: 2007-12-09
forum: Desktop Environments
---

### Post by asdel on 2007-12-09
Thunderbird starts slowly, taking 30 seconds or so start with no window being draw on the screen. It always starts successfully, it just hands for 30 seconds.

I am fairly certain this is something I goofed on with a desktop setting of so sort.

I've experienced this under 7.10 and 7.4. After installing Kubuntu 7.10, problem vanished. However, I've done an apt-get install ubuntu-desktop to switch over to gnome as my primary environment. I've been tinkering a lot of different GL-desktop settings. Now the problem has returned. However, disabling the GL-desktop does not make problem go away.

My thunderbird profile resides on an NFS/samba server. This provided sufficient performance because Thunderbird has been working fine under KDE.

This slowness persists past reboots.


Here is an strace showing the slowness:

mjs@Saaz:~$ strace -ttx thunderbird
...
08:45:22.179202 stat64("/usr/lib/thunderbird/init.d/S*", 0xbfe3df7c) = -1 ENOENT (No such file or directory)
08:45:22.179261 stat64("/home/mjs/.thunderbird/init.d/S*", 0xbfe3df7c) = -1 ENOENT (No such file or directory)
08:45:22.179338 clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e556f8) = 13813
08:45:22.182086 wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 13813
08:46:06.085144 --- SIGCHLD (Child exited) @ 0 (0) ---
08:46:06.085243 open("/home/mjs/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
08:46:06.085335 open("/usr/lib/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = -1 ENOENT (No such file or directory)
08:46:06.085420 stat64("/home/mjs/.thunderbird/init.d/K*", 0xbfe3df7c) = -1 ENOENT (No such file or directory)
08:46:06.085502 stat64("/usr/lib/thunderbird/init.d/K*", 0xbfe3df7c) = -1 ENOENT (No such file or directory)
08:46:06.085591 exit_group(0)           = ?
Process 13802 detached

---

