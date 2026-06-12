---
title: "thunderbird won't start automatically sometimes - where is the log?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by hachel on 2010-02-24
Hi,
I added thunderbird to the startup-applications under system->preferences->startup apps.
Sometimes it starts fine and sometimes it doesn't.
In which of the many logs can I check what went wrong?

---

### Post by dvlchd3 on 2010-02-24
I would just change the startup command to something like:

```

thunderbird > ~/tbird.log

```

This will put any errors normally printed to the console into the tbird.log file in your home directory.  I'm not sure if thunderbird normally logs anything anywhere else.  I know firefox is a pain to get any detailed debugging information out of... :-/

---

### Post by hachel on 2010-03-03
I've found out that thunderbird only doesn't start when I boot from a complete power off. When I merely reboot it starts.
I've tried with the log-file and it doesn't even create the file, whereas when I run that command in the terminal it creates it, empty though. Therefore in my opinion it looks like it doesn't run the command at all on startup.

Is there not a system-log I can check?

Cheers,

hachel

---

### Post by kellemes on 2010-03-03
Lot of logs in /var/log

---

