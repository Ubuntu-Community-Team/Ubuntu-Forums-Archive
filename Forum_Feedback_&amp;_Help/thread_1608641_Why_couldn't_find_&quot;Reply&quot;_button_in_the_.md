---
title: "Why couldn't find &quot;Reply&quot; button in the thread"
date: 2010-10-29
forum: Forum Feedback &amp; Help
---

### Post by Andy Chang on 2010-10-29
I'm new to this forums and Ubuntu. Yesterday I post a thread in this forum, but now I coudn't find the "Reply" button, where is it ?
Here is my thread: [http://wwww.ubuntuforums.org/showthread.php?t=1607936](http://wwww.ubuntuforums.org/showthread.php?t=1607936)

---

### Post by WorMzy on 2010-10-29
That thread is locked. Nobody can make replies to it.

---

### Post by matt_symes on 2010-10-29
Hi

The thread was closed by the moderator because it broke forum rules.

[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138")

Kind regards

---

### Post by CharlesA on 2010-10-29
Yep, that thread is closed.

If you've got a question about why a thread was closed, either PM the person who closed it or post in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

---

### Post by Andy Chang on 2010-10-29
> **matt_symes said:**
> Hi
 
The thread was closed by the moderator because it broke forum rules.
 
[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138")
 
Kind regards
 
**Which rule did I break?** You mean the administrator closed it? But I need reply the thread.

---

### Post by WorMzy on 2010-10-29
> **Andy Chang said:**
> **Which rule did I break?** You mean the administrator closed it? But I need reply the thread.

You were asking how to log in to the graphical environment as the root user. Any post showing you how to do this would be in beech of this:

> **Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.**

---

### Post by CharlesA on 2010-10-29
> **Andy Chang said:**
> **Which rule did I break?** You mean the administrator closed it? But I need reply the thread.

You were trying to log into the GUI as the root user, which is a bad idea.

The root account is locked by default in Ubuntu.

---

### Post by matt_symes on 2010-10-29
Hi

And you should not need to login as root anyway. Nobody on here will tell you how to do this. If you can explain why you _think_ you need to log on as root, they maybe we can explain why you don't need to and show you safe methods of achieving whatever it is you are trying to achieve.

Kind regards

---

### Post by Verbeck on 2010-10-29
if you want to run a command as root put sudo in front of the command in the terminal
to open nautilus as root(the filemanager) run sudo nautilus

---

### Post by Andy Chang on 2010-10-29
Got it. Sorry, I didn't say details. I'm not going to boot in Graphics mode by root user, I want ubuntu boot into **Text** **Mode** automatically! I'm a PC engineer, now I need test notebook under Linux text mode. I'd like ubuntu can boot into text mode then run the test automatically, like put the command in DOS autoexec.bat. Who can help me ? Thanks.

---

### Post by CharlesA on 2010-10-29
Make a new thread about that. Just don't have it login as root automatically, just use whatever user account you want.

---

### Post by sisco311 on 2010-10-29
> **Andy Chang said:**
> Got it. Sorry, I didn't say details. I'm not going to boot in Graphics mode by root user, I want ubuntu boot into **Text** **Mode** automatically! I'm a PC engineer, now I need test notebook under Linux text mode. I'd like ubuntu can boot into text mode then run the test automatically, like put the command in DOS autoexec.bat. Who can help me ? Thanks.

In order to disable the display manager, edit /etc/default/grub and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then run:```
sudo update-grub
```Not sure about the second part. If you want to run the *test* as a service, then write an Upstart job. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

If you want to enable autologin on a virtual console (tty) install **rungetty**. Edit the /etc/init/tty1.conf file to something like:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/rungetty tty1 --autologin YOUR_USER_NAME
```Enable the autologin for an admin user, add something like:
```
if [[ $(tty) = /dev/tty1 ]]; then
  sudo your_script_here
fi
```to its ~/.bashrc file. And edit the sudoers file to allow the user to run the command as root without a password. See [thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by Andy Chang on 2010-10-29
> **sisco311 said:**
> In order to disable the display manager, edit /etc/default/grub and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then run:```
sudo update-grub
```Not sure about the second part. If you want to run the *test* as a service, then write an Upstart job. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
 
If you want to enable autologin on a virtual console (tty) install **rungetty**. Edit the /etc/init/tty1.conf file to something like:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.
 
start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]
 
respawn
exec /sbin/rungetty tty1 --autologin YOUR_USER_NAME
```Enable the autologin for an admin user, add something like:
```
if [[ $(tty) = /dev/tty1 ]]; then
  sudo your_script_here
fi
```to its ~/.bashrc file. And edit the sudoers file to allow the user to run the command as root without a password. See [thread=1132821]HowTO: Sudoers Configuration[/thread]
 
Thanks for reply.
I had make system boot into text mode by changing GRUB file as you said. But what's the "**rungetty"** you mentioned. How to find it and install?

---

### Post by Elfy on 2010-10-29
This is not a support forum - see post #11. Your original query has been answered. Closed

---

### Post by CharlesA on 2010-10-29
rungetty is used for virtual terminals (tty)

But yeah, start a new thread please.

---

