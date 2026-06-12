---
title: "Desktop does not launch after login"
date: 2020-02-04
forum: Desktop Environments
---

### Post by askorski on 2020-02-04
Hi,

Since this morning, when my system starts, it displays the login screen as usual, but once my password typed the "cancel" and "next" buttons get disabled and nothing append. This is not a bad password issue since when I type a bad password it clearly indicates me the password is incorrect.

However I am still able to switch to another TTY with [Ctrl]+[Alt]+[F2], log in and run the [FONT=courier new]startx[/FONT] command.

I already found threads advising to reinstall [FONT=courier new]gdm3[/FONT] and [FONT=courier new]ubuntu-desktop[/FONT], but it did not help.
I also tried to remove [FONT=courier new]~/.Xauthority[/FONT] and [FONT=courier new]~/.ICEauthority[/FONT] without success.
Removing [FONT=courier new]/tmp[/FONT] had no effect.

Not being a sysadmin, I have no idea how to diagnose this problem.

Any help would be greatly appreciated.

I am running **Ubuntu 18.04**, let me know how to provide any other information to help resolve this issue.

---

### Post by askorski on 2020-02-04
I finally found the problem and will detail the way I investigated here in case it could help someone (maybe me) one day.

1. From the GUI login screen, Open a TTY with [Ctrl]+[Alt]+[2] and login
2. Go back to GUI with [Ctrl]+[Alt]+[1] and try to login
3. Return quickly to the TTY and execute [FONT=courier new]ls -lt /var/log | less[/FONT] which sorts files by modification date with the most recent on top
4. Watch for files modified recently (less than a minute ago), and look for something "weird" that could indicate what is failing

In my case, I found a line in the *auth.log* indicating that a *sync_tasks.sh* script was ran at session start: [FONT=courier new]Feb  4 15:09:05 n650du gdm-password]: pam_exec(gdm-password:session): Calling /usr/local/bin/sync_tasks.sh ...[/FONT]
This script aims at syncing task-warrior with my task-server.

But, last days I am migrating my old server to an other machine and being quite advanced in the process, I updated the DNS to make my domain target the new machine. This made the task-server unreachable causing an error at session start, preventing the desktop to launch...

It is a good lesson for me: a DNS update can cause my desktop not to start if I produce and use quick and dirty scripts...

---

