---
title: "Mathematica 7 crashes on startup"
date: 2009-03-02
forum: General Help
---

### Post by skintythe1andonly on 2009-03-02
Hi

I have just started encountering this problem when starting Mathematica 7. I have had it working fine for the last few weeks but all of a sudden today the notebook crashes on startup. I cant enter anything and none of the top buttons do anything. I have to force quit the program. The Math Kernel seems to start ok as I can run it in the non-gui mode from the terminal. This really is not the same as I mainly use it for graphics. 

Any ideas of how to identify the problem. I am using 64-bit intrepid. I have turned of compiz. When I run it from the terminal I do not get any errors, the notebook window just goes gray and does nothing.

---

### Post by skintythe1andonly on 2009-03-02
ok ive been trying to debug this but am not having much luck. I tried reinstalling it but that didnt work. I have now tried using strace to debug the problem of why it is hanging on startup

```
blah blah blah lots of reads......
..............
...........
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 1291
stat("/etc/fonts/fonts.conf", {st_mode=S_IFREG|0644, st_size=5283, ...}) = 0
open("/tmp/fonts1225.conf", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fcntl(1, F_DUPFD, 10)                   = 11
close(1)                                = 0
fcntl(11, F_SETFD, FD_CLOEXEC)          = 0
dup2(3, 1)                              = 1
close(3)                                = 0
stat("/usr/local/Wolfram/Mathematica/7.0/Executables/sed", 0x7fff5871c720) = -1 ENOENT (No such file or directory)
stat("/usr/bin/X11/sed", 0x7fff5871c720) = -1 ENOENT (No such file or directory)
stat("/usr/bin/sed", 0x7fff5871c720)    = -1 ENOENT (No such file or directory)
stat("/bin/sed", {st_mode=S_IFREG|0755, st_size=52344, ...}) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fd250701770) = 1295
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 1295
dup2(11, 1)                             = 1
close(11)                               = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fd250701770) = 1296
wait4(4294967295, 0x7fff5871c82c, 0, NULL) = ? ERESTARTSYS (To be restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(4294967295, 

```

AS you can see the "/usr/local/Wolfram/Mathematica/7.0/Executables/sed", "/usr/bin/sed", and "/usr/bin/X11/sed" dont seem to be present. Ive tried reinstalling sed with no luck. Im not quite sure what to do from here. I know i prob could create symbolic links to the directories but not sure really what im doing

---

### Post by skintythe1andonly on 2009-03-08
bump

---

