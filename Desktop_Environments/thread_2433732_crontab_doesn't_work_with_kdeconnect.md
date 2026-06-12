---
title: "crontab doesn't work with kdeconnect"
date: 2019-12-24
forum: Desktop Environments
---

### Post by jduns on 2019-12-24
I have successfully created a crontab job with a bash script in my home.
This is the crontab code:
```
30 8-11,15-18 * * * /home/duns/memento-bere.bash
```
This is the script code:
```
#!/bin/sh

play /home/duns/Music/memento.oga &&
zenity --info --display=:0.0 \
    --text="<span size=\"xx-large\">Time is $(date +%Hh%M)</span>\n\nricordati di <b>bere</b>." \
    --title="drink time"
```

But if I add a command like this ```
kdeconnect-cli --ping-msg "remember to drink!" -d [mydevice ID]
``` crontab stops working, even if I recall this command in an external bash script: ```
./memento-bere-send.sh
``` and even the script works perfectly (recalled from terminal o via Dolphin).

This is the error message:
```
(CRON) info (No MTA installed, discarding output)
```

Nothing to do by installing postfix, nor adding something like ```
>/dev/null 2>&1
``` to my crontab command.

---

### Post by TheFu on 2019-12-25
KDE tools probably assume a session and nothing in cron provides the extra session information.
Sorry.

You can check the differences in the two environments.
```
$ env > /tmp/full-session
```

```
1 * * * * /usr/bin/env >  /tmp/cron-session
```

Then compare those 2 output files. Lots of differences.

---

### Post by jduns on 2019-12-27
and so: what do you suggest? What should I do?

---

