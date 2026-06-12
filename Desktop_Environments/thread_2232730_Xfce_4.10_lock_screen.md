---
title: "Xfce 4.10 lock screen"
date: 2014-07-03
forum: Desktop Environments
---

### Post by theo5 on 2014-07-03
I cannot use "Lock Screen" - when i press it simply nothing happens.
I use Ubuntu 14.04 LTS with Xfe4.

I have already tried "refresh" my panel, by right click -> add -> etc.
using the default shortcut ctrl+alt+delete
and user@pc:~$ xflock4

Any ideas?

---

### Post by Toz on 2014-07-03
Are you talking about the "Lock Screen" option from the Action Buttons plugin or the Whisker Menu?

xflock4 is simply a shell script that looks for and runs, in this order:
- light-locker-command -l
- xscreensaver-command -lock
- gnome-screensaver-command --lock
- xlock -mode blank
- slock

I believe Ubuntu comes with gnome-screensaver. Can you check that its still installed? Also, try to manually run all of the 5 above commands to see if they work. Most likely you're missing a supported package to do the lock-screening.

---

### Post by theo5 on 2014-07-04
> **Toz said:**
> Are you talking about the "Lock Screen" option from the Action Buttons plugin or the Whisker Menu?

exactly


> **Toz said:**
> xflock4 is simply a shell script that looks for and runs, in this order:
- light-locker-command -l
- xscreensaver-command -lock
- gnome-screensaver-command --lock
- xlock -mode blank
- slock

I tried those commands.
user@pc:~$ xscreensaver-command -lock works but sometimes does not display the window where you are supposed to press the password, so i have to do it blindly.

I also reintalled ubuntu-screensaver from package manager, but still "Lock Screen" does not work. Is any way I can fix this or xflock4 command?

---

### Post by Toz on 2014-07-04
>  Are you talking about the "Lock Screen" option from the Action Buttons plugin or the Whisker Menu?> **theo5 said:**
> exactly
Which one? Action Buttons plugin or Whisker Menu?

> I tried those commands.
user@pc:~$ xscreensaver-command -lock works but sometimes does not display the window where you are supposed to press the password, so i have to do it blindly.

I also reintalled ubuntu-screensaver from package manager, but still "Lock Screen" does not work. Is any way I can fix this or xflock4 command?
What do the the following commands return?
```
ps -ef | grep session
```
```
ps -ef | grep screen
```
```
apt-cache policy xfce4-session
```
```
apt-cache policy light-locker
```
And what happens if you manually run:
```
xflock4
```
...in a terminal window?

---

### Post by theo5 on 2014-07-04
> **Toz said:**
> Which one? Action Buttons plugin or Whisker Menu?

Top-Right corner. I press the "user" button and then "Lock Screen". Nothing Happens. I also tried Right Click --> Panel --> Add New Items --> Action Buttons --> Add. But still when I press "Lock Screen" nothing happens.


> **Toz said:**
> What do the the following commands return?
```
ps -ef | grep session
```
```
ps -ef | grep screen
```
```
apt-cache policy xfce4-session
```
```
apt-cache policy light-locker
```
And what happens if you manually run:
```
xflock4
```
...in a terminal window?

```
ps -ef | grep session
```

```
theo      1625  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:12 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-EmOup4OAmV
theo      1646  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:06 upstart-dbus-bridge --daemon --session --user --bus-name session
theo      1667  1655  0 &#921;&#959;&#973;&#955;03 ?   00:00:03 xfce4-session
theo      1714  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
theo      1873  1667  2 &#921;&#959;&#973;&#955;03 ?   00:27:36 skype -session 218157fbf-8545-48fe-b42d-387bdd1c11aa_1404394741_63002
theo      1906  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:00 /usr/bin/kactivitymanagerd -session 26288fd28-ed1c-408c-9ac1-6219844df715_1404394741_63040
theo      2089  1452  1 &#921;&#959;&#973;&#955;03 ?   00:18:03 ktorrent -session 2d9447b40-937f-4f67-bad2-fdb6e2ba48c3_1404394741_63807
theo      2172  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:00 kget -session 2c508bbf7-ac27-4c98-8761-f239398c3d9e_1404394741_63019
root     19196  1452  0 12:19 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
theo     22036  9336  0 13:45 pts/0    00:00:00 grep --color=auto session 
```

"&#921;&#959;&#965;&#955;03" is the greek translation of July 03.

```
ps -ef | grep screen
```

```
theo      2262  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:02 xscreensaver -no-splash
theo     15436  1452  0 02:37 ?        00:00:00 light-locker --lock-after-screensaver=0 --lock-on-suspend --no-late-locking
theo     21293  1452  0 12:30 ?        00:00:00 /usr/bin/gnome-screensaver --no-daemon
theo     22047  9336  0 13:48 pts/0    00:00:00 grep --color=auto screen
```

```
apt-cache policy xfce4-session
```

```
xfce4-session:
  Installed: 4.10.1-3ubuntu5
  Candidate: 4.10.1-3ubuntu5
  Version table:
 *** 4.10.1-3ubuntu5 0
        500 http://gr.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status 
```

```
apt-cache policy light-locker
```

```
light-locker:
  Installed: 1.4.0-0ubuntu1
  Candidate: 1.4.0-0ubuntu1
  Version table:
 *** 1.4.0-0ubuntu1 0
        500 http://gr.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

xflock4 does completely nothing  :confused:

---

### Post by Toz on 2014-07-04
> xflock4 does completely nothing
...and by nothing, you mean it just returns control to the shell. No actions? no error messages?

> ps -ef | grep screen

theo      2262  1452  0 &#921;&#959;&#973;&#955;03 ?   00:00:02 xscreensaver -no-splash
theo     15436  1452  0 02:37 ?        00:00:00 light-locker --lock-after-screensaver=0 --lock-on-suspend --no-late-locking
theo     21293  1452  0 12:30 ?        00:00:00 /usr/bin/gnome-screensaver --no-daemon
You've got three screen saver programs all running - you should only really have one. Try killing the xscreensaver and light-locker processes, making sure they are still not running, then trying the lock screen function. If it doesn't work with gnome-screensaver, kill that process, restart one of the others and try again. Basically, try locking your screen with only one of the screensaver daemons running at any given time. Also make sure that the lock screen option is selected in the respective screensaver's preferences/settings.

---

### Post by theo5 on 2014-07-05
> **Toz said:**
> ...and by nothing, you mean it just returns control to the shell. No actions? no error messages?
Exactly.


> **Toz said:**
> You've got three screen saver programs all running - you should only really have one. Try killing the xscreensaver and light-locker processes, making sure they are still not running, then trying the lock screen function. If it doesn't work with gnome-screensaver, kill that process, restart one of the others and try again. Basically, try locking your screen with only one of the screensaver daemons running at any given time. Also make sure that the lock screen option is selected in the respective screensaver's preferences/settings.

I tried gnome-screensaver and xscreensaver working separately every time, but for the first I got a locked black screen - no screen saver. So I think I go with the second one.

Thank you very much for your help.

---

