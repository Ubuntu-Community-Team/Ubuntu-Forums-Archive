---
title: "Nautilus Hangs on Startup"
date: 2012-09-02
forum: Desktop Environments
---

### Post by linuxpyro on 2012-09-02
I'm running Ubuntu 12.04, 64 bit.  At some point not too long ago Nautilus stopped managing the desktop, so when I log in I get no folders or icons and can't get a menu when I right click.  (I think this may have started after I was saving a file in another program, and created a folder on the desktop.)  If I try to start Nautilus from the launcher in Unity, a window will open but will remain blank, trying to exit it will prompt me to force it close.

When I first log in, I can see that Nautilus is running by doing ps -aux | grep nautilus from the terminal.  If I kill it and try to run it manually from the terminal it will still hang, without any error messages or anything else other than the message "Initializing nautilus-gdu extension".  In case anyone is curious I tried running it with strace, and this is where it starts hanging:

```

brk(0x1b76000)                          = 0x1b76000
brk(0x1b6e000)                          = 0x1b6e000
pipe([19, 24])                          = 0
pipe([30, 31])                          = 0
pipe([32, 33])                          = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fe4e6b62c50) = 3317
close(24)                               = 0
close(31)                               = 0
close(33)                               = 0
read(19, "", 8)                         = 0
close(19)                               = 0
select(33, [30 32], NULL, NULL, NULL

```

Does anyone have any suggestions?  I tried deleting .local/share/gvfs-metadata, although this didn't help.  Everything else in Unity works fine, and no other applications seem to be having problems.

---

