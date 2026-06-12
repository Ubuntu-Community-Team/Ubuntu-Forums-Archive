---
title: "HOWTO: tunnel a desktop enviroment through SSH"
date: 2007-07-12
forum: Desktop Environments
---

### Post by maybeway36 on 2007-07-12
Besides offering the user a remote shell, SSH can also run X11 applications on a remote computer. This extends even to desktop environments such as GNOME and KDE, as they consist of a collection of separate applications.
I have used this method with two computers running Kubuntu 7.04. However, the computers do not necessarily need to run the same environment or even the same distribution.

1. On the server, install a desktop environment and OpenSSH server, if they are not already present. An X server is not required.
```
sudo aptitude install openssh-server
```
2. On the client, install an X server, the xterm terminal emulator, and the OpenSSH client. These should already be present on most distributions.
3. On the client, press Ctrl+Alt+F1 to show a terminal. Log in and type
```
xinit /usr/bin/xterm -- :1
```
to open a new X session (on “display 1”) with only a terminal on the screen.
Note: In distributions besides Ubuntu and Debian, the xterm executable may be in a different place. Use the command ```
whereis xterm
``` to find it.
4. In the new terminal, open an SSH connection to the server. Type:
```
ssh -Y username@hostname
```
replacing “username” with your login name on the server and “hostname” with the server's host name (or IP address.)
5. The SSH client will ask you for your server password. Enter it. :)
6. Now that you have a shell prompt, all you need to do is launch the desktop enviroment.
For GNOME: ```
gnome-session
```
For KDE: ```
startkde
```
For XFCE: ```
startxfce4
```
7. Now enjoy! Don't close the xterm window until you are done, and if the server doesn't close after you log out of GNOME/KDE, press Ctrl+Alt+Backspace to kill it.

---

