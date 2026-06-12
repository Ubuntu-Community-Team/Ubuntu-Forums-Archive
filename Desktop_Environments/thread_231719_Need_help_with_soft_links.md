---
title: "Need help with soft links"
date: 2006-08-07
forum: Desktop Environments
---

### Post by pbb on 2006-08-07
Hi,

I am doing my first bits of system organising so I get everything the way I want. I am definetly not very familiar with Linux yet.

I wish to store my Kopete chat logs on a central location on the network. Since I couldn't find any preferences for Kopete to change the location of the logs, I decided to create a softlink to the correct network location:

```
ln -s /media/fat/home/Peter/Internet/chat/logs/Kopete /home/peter/.kde/share/apps/kopete/logs
```

However, one time the network computer was not available while booting Ubuntu. The result seemed to be that the softlink disappeared, and Kopete used a "real" logs directory again. After restoring the network computer and rebooting Ubuntu, the logs directory stayed a real directory instead of a softlink.

Have I been using the correct technology to customize my folder structure, and how can I make sure my links to network folders persist?

Thanks, Peter

---

### Post by asimon on 2006-08-08
Well, the clean solution would be to have Kopete fixed that it allows to put the Logs somewhere else.

It seems if the Log file is not readable (happened when your sever was down) it creates them new.

A workaround would be to check during KDE start if your link still exists and recreate the link if not, i.e. you could put something like this
```

#!/bin/sh

LOG_FILE=/home/peter/.kde/share/apps/kopete/logs

# if the log file is no link, delete it and recreate the link
if [! -L $LOG_FILE ]; then
        rm -fr $LOG_FILE
        ln -s /media/fat/home/Peter/Internet/chat/logs/Kopete $LOG_FILE
fi

```
into ~/.kde/env/link_kopetes_log.sh . Scripts ending with .sh in the ~/.kde/env/ directory will be sources automatically during KDE startup. This directory doesn't exist be default, thus you will need to create it first (mkdir ~/.kde/env).

---

### Post by pbb on 2006-08-08
> **asimon said:**
> Well, the clean solution would be to have Kopete fixed that it allows to put the Logs somewhere else.

Hmmm can you explain that further? Do you mean Kopete has the ability to put logs somewhere else an my install of it is broken, or do you mean Kopete *should* have that ability and I should ask them to build it in? ;-)

> **asimon said:**
> It seems if the Log file is not readable (happened when your sever was down) it creates them new.

What actually happens is that the softlink (to a directory on the remote server) gets replaced by a physical directory, where the new logfiles are stored.

> **asimon said:**
> A workaround would be to check during KDE start if your link still exists and recreate the link if not, i.e. you could put something like this
```

#!/bin/sh

LOG_FILE=/home/peter/.kde/share/apps/kopete/logs

# if the log file is no link, delete it and recreate the link
if [! -L $LOG_FILE ]; then
        rm -fr $LOG_FILE
        ln -s /media/fat/home/Peter/Internet/chat/logs/Kopete $LOG_FILE
fi

```
into ~/.kde/env/link_kopetes_log.sh . Scripts ending with .sh in the ~/.kde/env/ directory will be sources automatically during KDE startup. This directory doesn't exist be default, thus you will need to create it first (mkdir ~/.kde/env).

Thanks! That is the kind of help I needed. Not having any experience in shell scripting, but I had a feeling my solution would lie in that direction.

I will have a look if I can modify the script to support softlinked directories, and if I can move the log to the server when it's up again...

---

### Post by asimon on 2006-08-08
> **pbb said:**
> Hmmm can you explain that further? Do you mean Kopete has the ability to put logs somewhere else an my install of it is broken, or do you mean Kopete *should* have that ability and I should ask them to build it in? ;-)

The second, kopete hasn't that ability.

> **pbb said:**
> 
I will have a look if I can modify the script to support softlinked directories, and if I can move the log to the server when it's up again...
The script should work no matter if /home/peter/.kde/share/apps/kopete/logs is a directory or file.

---

