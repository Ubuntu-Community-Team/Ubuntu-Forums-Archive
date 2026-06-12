---
title: "ssh-agent running but not working"
date: 2009-06-05
forum: General Help
---

### Post by darkpixel on 2009-06-05
I have a few Ubuntu machines between home and work.
All my workstations are running 9.04.

At home, after I first boot and try to ssh anywhere, I get a GUI pop-up asking for the password for my ssh key.  After it's entered, I can ssh into any box without asking for a password.

On my work laptop I am asked (in gnome-terminal) every time I ssh.

From my work laptop:
aaron@uitlinux42:~$ ps ax | grep -i ssh
 2775 ?        Ss     0:00 /usr/sbin/sshd
 4641 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 9125 pts/6    S+     0:00 grep -i ssh
aaron@uitlinux42:~$ 

My home workstation looks the same.

I've also tried checking ssh_config in my ~/.ssh/ folder, but it doesn't exist on either machine.  /etc/ssh/ssh_config has nothing appropriate either.

Anyone have pointers on debugging the issue?

---

