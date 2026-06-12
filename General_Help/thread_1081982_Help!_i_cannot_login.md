---
title: "Help! i cannot login"
date: 2009-02-27
forum: General Help
---

### Post by obaid on 2009-02-27
i have Ubuntu 8.10 installed on IBM thinkpad X61 laptop with all updates, kernel 2.6.27-11 generic. (no dual boot, no M$ w1nd0wz)

i have been using ubuntu last 3 months with no problem.

last night, i installed some packages required for metasploit.
and after reboot, i only see an empty brown screen with mouse pointer busy.i can move mouse.

here are log files:

[LIST]
[*][SIZE="3"]auth.log[/SIZE]
[/LIST]
> Feb 27 12:53:23 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 12:53:33 X61 last message repeated 10 times
Feb 27 12:53:34 X61 login[5383]: pam_unix(login:session): session opened for user onaogh by LOGIN(uid=0)
Feb 27 12:53:35 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 12:54:06 X61 last message repeated 26 times
Feb 27 12:55:07 X61 last message repeated 62 times
Feb 27 12:56:08 X61 last message repeated 58 times
Feb 27 12:57:10 X61 last message repeated 55 times
Feb 27 12:58:12 X61 last message repeated 64 times
Feb 27 12:59:13 X61 last message repeated 54 times
Feb 27 13:00:13 X61 last message repeated 55 times
Feb 27 13:01:12 X61 last message repeated 53 times
Feb 27 13:02:13 X61 last message repeated 57 times
Feb 27 13:03:12 X61 last message repeated 64 times
Feb 27 13:04:12 X61 last message repeated 61 times
Feb 27 13:05:12 X61 last message repeated 52 times
Feb 27 13:06:13 X61 last message repeated 57 times
Feb 27 13:07:12 X61 last message repeated 51 times
Feb 27 13:08:12 X61 last message repeated 54 times
Feb 27 13:09:13 X61 last message repeated 54 times
Feb 27 13:10:13 X61 last message repeated 54 times
Feb 27 13:11:13 X61 last message repeated 58 times
Feb 27 13:12:13 X61 last message repeated 54 times
Feb 27 13:13:13 X61 last message repeated 57 times
Feb 27 13:14:12 X61 last message repeated 55 times
Feb 27 13:15:13 X61 last message repeated 54 times
Feb 27 13:16:13 X61 last message repeated 62 times
Feb 27 13:17:01 X61 last message repeated 41 times
Feb 27 13:17:01 X61 CRON[13893]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 27 13:17:01 X61 CRON[13893]: pam_unix(cron:session): session closed for user root
Feb 27 13:17:02 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 13:17:11 X61 last message repeated 8 times
Feb 27 13:17:11 X61 sudo:   onaogh : TTY=tty1 ; PWD=/home/onaogh ; USER=root ; COMMAND=/usr/bin/killall login
Feb 27 13:17:13 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 13:17:43 X61 last message repeated 28 times
Feb 27 13:18:43 X61 last message repeated 53 times
Feb 27 13:19:18 X61 last message repeated 36 times
Feb 27 13:19:18 X61 login[14009]: pam_unix(login:session): session opened for user onaogh by LOGIN(uid=0)
Feb 27 13:19:19 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 13:19:50 X61 last message repeated 29 times
Feb 27 13:20:24 X61 last message repeated 36 times
Feb 27 13:20:25 X61 sudo:   onaogh : TTY=tty1 ; PWD=/home/onaogh ; USER=root ; COMMAND=/bin/mount /dev/sdb1 /mnt
Feb 27 13:20:26 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username
Feb 27 13:20:51 X61 last message repeated 25 times


as you see in auth.log, when i sudo killall login, login spawns but same empty brown screen with busy cursor.

i tryed to boot in recovery mode and open root shell, then start /etc/init.d/gdm start, but it is same.

i tryed to stop and start gdm service, but same result.

other log files (dmesg.0, Xorg.0, kern.log, daemon.log) are attached(attachment gives some error):
rapidshare link: 

[http://rapidshare.com/files/203145968/logfiles.zip.html](http://rapidshare.com/files/203145968/logfiles.zip.html)

---

### Post by Peter09 on 2009-02-27
Try recovery mode and

```
startx
```

---

### Post by obaid on 2009-02-27
tried startx in both recovery mode and normal mode

Ctrl+Shift+Alt+F1

then login

then sudo killall gdm (because it is already running)

startx

i get these errors:
Nautilus: Nautilus cannot be used now, due to an unexpected error.

another error dialogue.

The Panel has encountered a fatal error.

---

### Post by obaid on 2009-02-27
do u think this is something related to:
> Feb 27 13:20:26 X61 gdm[5189]: pam_nologin(gdm:auth): cannot determine username

---

### Post by Peter09 on 2009-02-27
OK, you most probably can restart nautilus by typing in a terminal
```
nautilus &
```

but this is not a real problem as yu can manage without it.


Have a look around

System->Administration->User and Groups

---

### Post by obaid on 2009-02-27
when i start my laptop - it stops at login screen, there is an empty brown screen with cursor only. nothing else. i cannot login.

if i Ctrl+Alt+Shift+F1 and killall gdm then startx, my background picture appears with nothing else, except 2 windows saying errors as i posted above.

i have posted my log files - i want to know the source of problem to solve, the last line at auth.log says:
> gdm[5189]: pam_nologin(gdm:auth): cannot determine username

what i can understand from that, googling it doesnt give much answer.

---

### Post by Peter09 on 2009-02-27
Been Googling as well.

try running

```
gdmsetup
```

in the command shell.

---

### Post by obaid on 2009-02-27
tried in recovery mode in root shell
tried in normal mode, same output.

> (gdmsetup:4610): Gtk-WARNING **: cannot open display:

do i have to reinstall ubuntu :(

---

### Post by Peter09 on 2009-02-27
Try this thread

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4](http://ubuntuforums.org/showpost.php?p=3605925&postcount=4)

---

