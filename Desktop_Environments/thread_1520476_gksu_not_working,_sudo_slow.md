---
title: "gksu not working, sudo slow"
date: 2010-06-29
forum: Desktop Environments
---

### Post by luke_lukem on 2010-06-29
Hi everyone, 
I've been having a problem with administrative apps all the way from last years' distros, and in 10.04-x64 it's still here.

When i launch an application that needs gksu, it simply hangs waiting for a gksu window that never shows up.
If i launch another administrative app, it hangs as well.
When i look at the process list, i get a lot of gksu instances, all sleeping.

if i kill those processes, the mentioned apps resume with an authentication error

But if i use a terminal and type sudo <app>, it hangs for a few seconds, then prompts for password and it works fine.

I don't know why it works so badly, but it needs to be fixed soon, many new users will surely find this very frustrating.

PD: i run ubuntu 10.04-64bit on a AMD-Athlon-x2

Cheers to all.

---

### Post by mprice on 2010-06-29
Have you tried using ```
gksudo
``` instead of ```
gksu
```

---

### Post by XSAlliN on 2010-06-29
It's not that an application needs gksu, if that would be case you wouldn't be able to use it with sudo...

**sudo** uses users configuration files with root privileges, which could affect permissions.

**gksu** uses root's configuration files with root privileges, which doesn't affect user.

**[...as stated here:]("http://www.psychocats.net/ubuntu/graphicalsudo")**

---

### Post by luke_lukem on 2010-07-01
Hi again,
i tried editing the "root terminal" menu launcher to use gksu:
<code>gksudo /usr/bin/x-terminal-emulator<\code>
but i get the same issue, it hangs and i must eventually kill it.
Afterwards, my /var/log/auth.log has this at the end:
<code>
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): conversation failed
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): auth could not identify password for [alfredo]
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): conversation failed
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): auth could not identify password for [alfredo]
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): conversation failed
Jul  1 20:22:41 ubuntu sudo: pam_unix(sudo:auth): auth could not identify password for [alfredo]
Jul  1 20:22:41 ubuntu sudo:  alfredo : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/alfredo ; USER=root ; COMMAND=/usr/bin/x-terminal-emulator
<\code>

Thanks for your help :)

---

### Post by jlotspeich34 on 2010-07-17
I'm running the same architecture and getting the same problem.  It just started about two weeks ago.


```
 
uname -rm
2.6.32-23-generic x86_64

```GKsu version 2.0.2


```
gksu -d gedit 2> temp.out
```results in 
```

No ask_pass set, using default!
xauth: /tmp/libgksu-qfqzWI/.Xauthority
STARTUP_ID: gksu/gedit/24568-0-hostname_TIME621972412
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
.
.
.

```No prompt appears.  Sudo seems to work just fine.

---

