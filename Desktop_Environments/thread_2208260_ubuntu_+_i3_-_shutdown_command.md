---
title: "ubuntu + i3 - shutdown command"
date: 2014-02-27
forum: Desktop Environments
---

### Post by tango2 on 2014-02-27
Hello,

I recently decided to give i3 a try and installed it on my ubuntu laptop. I have spend some time both using it and trying to tweak it, and i absolutely love it. 

However, the i3 only contains a command for logout and not quit, so i found a small script for boot shutting down and rebooting.

```

shutdown)
        systemctl poweroff
        ;;

```

but ubuntu does not implement the systemctl. How can i create a script that could shuts down / reboots without it?

---

### Post by lukeiamyourfather on 2014-02-27
The command I typically use is this.

```
sudo shutdown -h now
```

---

### Post by tango2 on 2014-03-08
That definitely does the trick, but is it possible to add the "sudo command" in a shortcut, so i dont have to start a terminal and type the password.

Probably a bit demanding now. :)

---

### Post by 3rdalbum on 2014-03-08
Use 'gksudo halt' in a script, or make the script owned by root and use the 'setuid' permission to make the script run as root automatically.

---

