---
title: "Why does my Desktop directory keep vanishing"
date: 2023-09-12
forum: Desktop Environments
---

### Post by davehk on 2023-09-12
Several time now when logging in after a boot my $Home directory have been displayed on the desktop.
This happens because my $HOME/Desktop directory has disappeared, resulting in XDG_DESKTOP_DIR="$HOME/Desktop" being changed to XDG_DESKTOP_DIR="$HOME/" in .config/user-dirs.dirs
Recreating the Desktop directory and resetting the XDG_DESKTOP_DIR value fixes the problem, but I don't understand why it is happening in the first place?

In the log I am seeing this:
```

/home/dave/Desktop was removed,  reassigning DESKTOP to homedir
```

immediately after:
```

Starting GNOME Shell on X11...
Reached target GNOME Session Manager is ready.
```



Any suggestions as to why this is happening would be welcome.


Thanks.

---

### Post by jmnorvell on 2023-10-06
Did you solve this? It happened to me today. Can you tell me the steps you took to do this temporary fix?:

"Recreating the Desktop directory and resetting the XDG_DESKTOP_DIR value fixes the problem"

John

---

### Post by liono87 on 2023-10-06
Check this link out. [https://askubuntu.com/questions/1429782/getting-error-too-many-levels-of-symbolic-links-when-trying-to-navigate-ubuntu](https://askubuntu.com/questions/1429782/getting-error-too-many-levels-of-symbolic-links-when-trying-to-navigate-ubuntu) .. Since a powercut, I faced the same issue every now and then. I get an error saying too many symbolic links to directorys Download/Music.. I saw an answer on stackoverflow and fixed it. Unfortunately, I cant find that link anymore. It suggested something like adding the missing directories below the user-dirs.dir file in .config directory again..However that doesnt work for me. I removed all n reboot. Voila!!

---

