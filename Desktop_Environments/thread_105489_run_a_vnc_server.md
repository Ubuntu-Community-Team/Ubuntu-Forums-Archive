---
title: "run a vnc server"
date: 2005-12-18
forum: Desktop Environments
---

### Post by talz13 on 2005-12-18
Sorry for the crosspost, but I replied in the [howto](http://ubuntuforums.org/showthread.php?t=45565) already, but thought it would be better off here:


Well, what I had going on my FC3 install that I just formatted was a vnc user that would be logged in at startup (the local monitor still shows the login screen, but the user is active), all the users session programs would start up (I had azureus run on login), and I could connect to the users desktop via vnc to perform tasks and such.

Neither of these guides seems to do quite what I'm looking for. I believe I followed this guide under FC3:
[http://www.fedoraforum.org/forum/showthread.php?t=42062](http://www.fedoraforum.org/forum/showthread.php?t=42062)
but config files and stuff are different from FC3

So any way to get a single VNC user active at boot, with his gnome session started automatically, and be able to log on from VNC or locally, like I used to have set up?

---

### Post by talz13 on 2005-12-19
Is there any way to get this working?  I started up the remote desktop yesterday, and hope that I don't have to restart, but the remote desktop is horribly, horribly slow.  I mean slow like I drag my mouse across the screen, and the pointer moves about 2 or 3 seconds later.  Very annoying for controlling it!

---

### Post by talz13 on 2005-12-19
[QUOTE=talz13]Is there any way to get this working?  I started up the remote desktop yesterday, and hope that I don't have to restart, but the remote desktop is horribly, horribly slow.  I mean slow like I drag my mouse across the screen, and the pointer moves about 2 or 3 seconds later.  Very annoying for controlling it![/QUOTE]

Well, I just did a ps aux to check my running processes for something completely unrelated, and found that vino is using 96.9% of my CPU:

```

jeff@server:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
jeff     27397  1.4  7.8 411072 81564 pts/0    Sl   Dec18  17:03 /usr/lib/j2re1.5-sun/bin/jav
**jeff     28131 96.9  0.9  20388 10048 ?        R    Dec18 1150:11 /usr/lib/vino/vino-server -**
root      9159  0.0  0.1   6280  1948 ?        Ss   Dec18   0:00 sshd: jeff [priv]
jeff      9165  0.0  0.1   6280  2036 ?        S    Dec18   0:00 sshd: jeff@pts/3
jeff      9166  0.0  0.1   4672  2032 pts/3    Ss   Dec18   0:00 -bash
root      9183  0.0  0.0   3428   972 pts/3    S    Dec18   0:00 su
root      9189  0.0  0.1   4152  1820 pts/3    S+   Dec18   0:00 bash
root      9375  0.0  0.1   4180  1276 ?        Ss   Dec18   0:00 /usr/sbin/squid -D -sYC
proxy     9377  0.0  0.8  10304  8492 ?        S    Dec18   0:05 (squid) -D -sYC
proxy     9379  0.0  0.0   1408   296 ?        Ss   Dec18   0:00 (unlinkd)
root      9970  0.0  0.1   6696  2028 ?        Ss   Dec18   0:00 /usr/sbin/nmbd -D
root      9972  0.0  0.2   8960  2696 ?        Ss   Dec18   0:00 /usr/sbin/smbd -D
root      9973  0.0  0.2   8960  2680 ?        S    Dec18   0:00 /usr/sbin/smbd -D
jeff     10002  0.0  0.2   9224  2992 ?        S    Dec18   0:00 /usr/sbin/smbd -D
cupsys   31671  0.0  0.3   7628  3424 ?        SNs  07:37   0:10 /usr/sbin/cupsd -F
syslog    4838  0.0  0.0   1764   792 ?        SNs  08:11   0:00 /sbin/syslogd -u syslog
root      7251  0.0  0.1   6284  1952 ?        Ss   11:55   0:00 sshd: jeff [priv]
jeff      7274  0.0  0.1   6436  2068 ?        S    11:55   0:00 sshd: jeff@pts/4
jeff      7275  0.0  0.2   4680  2076 pts/4    Ss   11:55   0:00 -bash
jeff     25019  0.0  0.1   3864  1040 pts/4    R+   13:48   0:00 ps aux

```

which might explain why it's acting so slow while I'm connected to it (this 96% is just being connected via putty, no VNC clients are currently connected to the machine)  Any clue as to what would make vino so processor hungry?

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=talz13]Well, I just did a ps aux to check my running processes for something completely unrelated, and found that vino is using 96.9% of my CPU:

```

jeff@server:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
jeff     27397  1.4  7.8 411072 81564 pts/0    Sl   Dec18  17:03 /usr/lib/j2re1.5-sun/bin/jav
**jeff     28131 96.9  0.9  20388 10048 ?        R    Dec18 1150:11 /usr/lib/vino/vino-server -**
root      9159  0.0  0.1   6280  1948 ?        Ss   Dec18   0:00 sshd: jeff [priv]
jeff      9165  0.0  0.1   6280  2036 ?        S    Dec18   0:00 sshd: jeff@pts/3
jeff      9166  0.0  0.1   4672  2032 pts/3    Ss   Dec18   0:00 -bash
root      9183  0.0  0.0   3428   972 pts/3    S    Dec18   0:00 su
root      9189  0.0  0.1   4152  1820 pts/3    S+   Dec18   0:00 bash
root      9375  0.0  0.1   4180  1276 ?        Ss   Dec18   0:00 /usr/sbin/squid -D -sYC
proxy     9377  0.0  0.8  10304  8492 ?        S    Dec18   0:05 (squid) -D -sYC
proxy     9379  0.0  0.0   1408   296 ?        Ss   Dec18   0:00 (unlinkd)
root      9970  0.0  0.1   6696  2028 ?        Ss   Dec18   0:00 /usr/sbin/nmbd -D
root      9972  0.0  0.2   8960  2696 ?        Ss   Dec18   0:00 /usr/sbin/smbd -D
root      9973  0.0  0.2   8960  2680 ?        S    Dec18   0:00 /usr/sbin/smbd -D
jeff     10002  0.0  0.2   9224  2992 ?        S    Dec18   0:00 /usr/sbin/smbd -D
cupsys   31671  0.0  0.3   7628  3424 ?        SNs  07:37   0:10 /usr/sbin/cupsd -F
syslog    4838  0.0  0.0   1764   792 ?        SNs  08:11   0:00 /sbin/syslogd -u syslog
root      7251  0.0  0.1   6284  1952 ?        Ss   11:55   0:00 sshd: jeff [priv]
jeff      7274  0.0  0.1   6436  2068 ?        S    11:55   0:00 sshd: jeff@pts/4
jeff      7275  0.0  0.2   4680  2076 pts/4    Ss   11:55   0:00 -bash
jeff     25019  0.0  0.1   3864  1040 pts/4    R+   13:48   0:00 ps aux

```

which might explain why it's acting so slow while I'm connected to it (this 96% is just being connected via putty, no VNC clients are currently connected to the machine)  Any clue as to what would make vino so processor hungry?[/QUOTE]

Maybe it started a screensaver?

---

### Post by talz13 on 2005-12-19
[QUOTE=cwaldbieser]Maybe it started a screensaver?[/QUOTE]

I thought I told it not to run a screensaver, but I suppose it could be doing it.

I think I remembered how I went about the vnc server before.  I must have set it up to run vncserver :1 at default runlevel, and then logged in and set my session programs from the gnome session that was launched.

I'm going to go try that now...

---

