---
title: "How to restart gnome-power-manager by cron?"
date: 2011-08-21
forum: Desktop Environments
---

### Post by thunderamur on 2011-08-21
Have an old bug with memory leak in gnome-power-manager in my Ubuntu Lucid 64-bit. It eat more than 100MB of RAM for some day. I entered in terminal "killall gnome-power-manager" and than "Alt+F2 + gnome-power-manager" to restart this daemon. I want to put this simple operations in cron.

1. I created script to restart
```
#!/bin/bash
killall gnome-power-manager
gnome-power-manager&
```I tried this script in terminal - passed.

2. I added the row to cron by "sudo crontab -e"
```
*/1 * * * * /home/thunder/soft/restart-gnome-power-manager
```I waited for a minute and saw that process of gnome-power-manager was killed, but new one was not created.

I think I make mistake in script. How to launch gnome-power-manager by cron?

---

### Post by papibe on 2011-08-21
Try this:
```
*/1 * * * * env DISPLAY=:0 /home/thunder/soft/restart-gnome-power-manager
```
Read about it in the section 'GUI Applications' on the [Crontab Howto]("https://help.ubuntu.com/community/CronHowto").

Regards.

---

### Post by thunderamur on 2011-08-21
I already tried it earlier. But I will try again.

Thx for a link.

---

### Post by thunderamur on 2011-08-21
Main mistake is gnome-system-manager, it do not show all processes by default and I simple do not saw than gnome-power-manager start from root!

I saw this when decided to use "ps aux"

```
thunder@athlon:~$ ps aux | grep gnome-power-manager
root     16599  0.1  0.2 165768  8240 ?        S    17:10   0:00 gnome-power-manager
thunder  16643  0.0  0.0   7692   824 pts/0    S+   17:10   0:00 grep gnome-power-manager

```Than I launch gnome-power-manager by Alt+F2 and saw

```
thunder@athlon:~$ ps aux | grep gnome-power-manager
root     16599  0.1  0.2 165768  8240 ?        S    17:10   0:00 gnome-power-manager
thunder  16677  1.0  0.2 167732  8740 ?        S    17:10   0:00 gnome-power-manager
thunder  16683  0.0  0.0   7692   824 pts/0    S+   17:10   0:00 grep gnome-power-manager

```And understand that I need

```
#!/bin/bash
killall gnome-power-manager
gnome-power-manager&
```

But "crontab" must be from user

crontab -e
```
0 8 * * * env DISPLAY=:0 /home/thunder/soft/restart-gnome-power-manager
```

:guitar:

Thx a lot :)

---

