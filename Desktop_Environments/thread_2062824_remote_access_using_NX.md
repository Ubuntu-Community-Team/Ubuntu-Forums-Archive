---
title: "remote access using NX"
date: 2012-09-25
forum: Desktop Environments
---

### Post by oregonbob on 2012-09-25
I often use the NX application from nomachine.com to remote access to Ubuntu gnome, unity and xfce desktops, utilizing ssh port for encryption/access. From my experience nothing else comes close in performance or experience. There is one bug I find very frustrating, that is that Ubuntu does not think an NX is a secure terminal (such as the console) so it will not allow menu choices such as users-admin, shutdown/restart. I have found a workaround by ignoring menu choices, jumping to a terminal session and then using "gksu command" instead of choosing from the menu. For example from a terminal session command line I can "gksu nohup shutdown -r now &" to restart the system.

It sure would be nice if I could get Ubuntu to think the terminal ID of an NX session is secure and therefore allow administrative apps. If I login via NX and do a 'tty' command it shows my terminal connection as "/dev/pts/2". In the old days you could add the tty device names to a file in /etc so they are recongized as secure for admin, but that doesn't work anymore.

Has anyone figured out how to enable administrative apps to work in NX?

---

