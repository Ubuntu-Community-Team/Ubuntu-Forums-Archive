---
title: "How do I restart syslog?"
date: 2005-10-05
forum: Desktop Environments
---

### Post by hanzj on 2005-10-05
Hello, I'm following the steps at [http://synce.sourceforge.net/synce/usb_linux_debug.php](http://synce.sourceforge.net/synce/usb_linux_debug.php), and I need to do step 3:
[INDENT]Restart syslog:
/etc/init.d/sysklogd restart (e.g. Debian)[/INDENT]
When I do that command, I get:
* Restarting system log daemon...
[COLOR="#ff0000"]*[/COLOR]slogd: Already running.                                                                         [[COLOR="Red"]fail[/COLOR]]



What must I do?

By the way, is this the right forum to post this thread?

---

### Post by KingBahamut on 2005-10-05
can you do a 

ps aux | grep -i logd 

and output those results?

---

### Post by hanzj on 2005-10-05
Dear Bill, Thanks for your response. 

Results of **ps aux | grep -i logd**

syslog    5110  0.0  0.2   1740   632 ?        Ss   Oct05   0:00 /sbin/syslogd -u syslog
root      5125  0.0  0.1   1552   320 ?        Ss   Oct05   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5127  0.0  0.1   2440   484 ?        Ss   Oct05   0:00 /sbin/klogd -P /var/run/klogd/kmsg
hanzj     12415  0.0  0.2   3772   756 pts/0    S+   00:33   0:00 grep -i logd

---

### Post by KingBahamut on 2005-10-05
so what happens when you 

/etc/init.d/syslogd stop
/etc/init.d/syslogd start

????

---

### Post by hanzj on 2005-10-05
hanzj@ubuntu:~$ /etc/init.d/syslogd stop
bash: /etc/init.d/syslogd: No such file or directory

---

### Post by heimo on 2005-10-05
How about:
```
sudo /etc/init.d/sys**k**logd stop
sudo /etc/init.d/sys**k**logd start

```

---

### Post by hanzj on 2005-10-05
Heimo, your suggestion works, but how do I know whether this abides with the instructions at [http://synce.sourceforge.net/synce/usb_linux_debug.php](http://synce.sourceforge.net/synce/usb_linux_debug.php), specifically, step 4?

My /var/log/all.log now says this:
Oct  6 00:59:47 localhost syslogd 1.4.1#16ubuntu6: restart.
Oct  6 01:00:09 localhost sudo:     hanzj : TTY=pts/0 ; PWD=/home/hanzj ; USER=root ; COMMAND=/usr/bin/gedit

I want to follow the steps given by the programmers of synce so that I can give them the information that they need to help me set up this program on my ubuntu.

---

### Post by heimo on 2005-10-05
Just follow the rest of instructions, but prefix rmmod and modprobe commands with sudo (super user do = root privileges). Not sure about other commands in those instructions.

---

### Post by hanzj on 2005-10-05
referring to my original post, why can't /etc/init.d/sysklogd restart work as it should?

---

### Post by heimo on 2005-10-05
[quote=hanzj]referring to my original post, why can't /etc/init.d/sysklogd restart work as it should?[/quote] 
You need to have root privileges to do that (on any Linux/unix system). To do that you either use su* to become root, or sudo -s to become root or prefix command with sudo to use root privileges for just that command.

Try
```
sudo -s
/etc/init.d/sysklogd restart
``` Works, right? Then write exit or hit ctrl+d to become regular user (type whoami to confirm) and run:

```
sudo /etc/init.d/sysklogd restart

``` Works. :)


*) doesn't work on default Ubuntu install unless you have given root a password later on

---

### Post by hanzj on 2005-10-05
heimo, [you're right]("http://ubuntuforums.org/showpost.php?p=388737&postcount=10")!
How come you didn't tell me that in the first place? (Insert inane smiley face here)
Thanks. Synce devs will be happy to now that newbie hanzj is following the instructions.

---

### Post by hanzj on 2005-10-05
Hey heimo,
I'm curious as to why you have the letter **k** in sys**k**logd in bold.
This is in regards to [Post#6]("http://ubuntuforums.org/showpost.php?p=388691&postcount=6")

---

### Post by heimo on 2005-10-05
Because of your post #5 where you missed letter k - just to emphasize correct spelling.  :) BTW, try tabulator completion - type beginning of command or filename and hit tabulator key to complete. If the rest of name is ambiguous, hit tab twice to get list of the hits and type couple more letters and use tab again.

---

### Post by hanzj on 2005-10-05
RE: post 13 from heimo
Another useful tip. Thanks again.

---

