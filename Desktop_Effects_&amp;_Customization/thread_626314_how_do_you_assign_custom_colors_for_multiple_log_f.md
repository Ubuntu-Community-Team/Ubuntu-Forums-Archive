---
title: "how do you assign custom colors for multiple log file tail output?"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by flaggh on 2007-11-28
How do I go about assigning different colors to different tail outputs of a log file?  I would like to try and have tail following multiple log files at once in a single terminal screen and color code which log file is which.  I have no problems getting multiple log files to tail continuously by running:
```

tail -f /var/log/dmesg &
tail -f /var/log/messages &
tail -f /var/log/syslog
```

but it would be preferable if /var/log/dmesg output was red, while /var/log/messages was green, and /var/log/syslog was blue, for example.

I didn't want to use conky for tailing the logs since I don't want conky taking up half my desktop, but I wouldn't mind a transparent terminal in the background doing this.

I tried:
```
 echo -e "\033[31m $(tail -f /var/log/dmesg &)"
```
and all this did was prevent me from doing anything in my terminal.

Any suggestions?  Thanks in advance.

---

