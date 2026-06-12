---
title: "E233: cannot open display"
date: 2006-09-26
forum: Desktop Environments
---

### Post by wittyguysuku on 2006-09-26
I have established a ssh session with a remote server. But later on when I try opening the source code in that server with gvim, I'm getting the following error. > E233: cannot open display. Later I tried giving **xhost +**. Even then this problem persist for opening an **xterm&**. Could you please help me out?

thanks!
Wg

---

### Post by wittyguysuku on 2006-09-27
Eureka!
Google helped me to find the solution for this problem!

Let me explain the steps that I followed to resolve this issue.

1) Edit **/etc/gdm/gdm.conf-custom** file
2) Under **security** section, it should look like: > [security]
security/DisallowTCP=false
3) Either do gdm-restart or gdm-safe-restart or Alt+Backspace and relogin again.
4) Either you can use > xhost + or edit **/etc/hosts.allow**

That's it!
Login to your remote machine using **ssh -X <remoteMachineIP>** or establish a **telnet** session. Giving xterm& will open a new window in your desktop.

:)

---

