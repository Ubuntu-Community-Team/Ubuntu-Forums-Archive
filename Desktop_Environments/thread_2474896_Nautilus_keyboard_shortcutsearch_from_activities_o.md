---
title: "Nautilus keyboard shortcut/search from activities overview not working"
date: 2022-05-11
forum: Desktop Environments
---

### Post by faust99 on 2022-05-11
Nautilus has started playing on my machine - it was all good but all of a sudden I've noticed two problems:

1. Links to files/folders from the activities overview do not work (nothing happens);
2. My keyboard shortcut to Nautilus has stopped working.

I'm on Ubuntu 22.04 Jammy with Gnome.

Please advise.

---

### Post by vanadium on 2022-05-11
1) Provide examples of such links/folders, and how you created these.
2) Does this persist after reboot? Is the shortcut still defined in Settings - Keyboard?

---

### Post by faust99 on 2022-05-11
1) You press the Super key and search for something --> click on a result (e.g. a file or folder with that name) --> nothing happens.
2) Yes, it's persistent after reboot and yes it's still defined.

---

### Post by faust99 on 2022-05-23
Bump.

---

### Post by vanadium on 2022-05-24
Does nautilus launch when started from the command line, and what is the output in the terminal? What happens if you type "xdg-open ~" in the terminal, and are there messages?

---

### Post by faust99 on 2022-05-24
Yes, it opens from the command line and there is no output in the terminal. 

"xdg-open~" yields:

> grep: /proc/sys/fs/binfmt_misc/WSLInterop: No such file or directory
WSL Interopability is disabled. Please enable it before using WSL.
grep: /proc/sys/fs/binfmt_misc/WSLInterop: No such file or directory
[error] WSL Interoperability is disabled. Please enable it before using WSL.
/usr/bin/wslview: line 216: /mnt/1E6C251C6C24EFE7/Windows/System32/reg.exe: cannot execute binary file: Exec format error
/usr/bin/wslview: line 308: [: -ge: unary operator expected
[error] This protocol is not supported before version 1903.


---

