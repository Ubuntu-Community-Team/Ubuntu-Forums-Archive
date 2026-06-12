---
title: "Cron Issue in Ubuntu 6.06"
date: 2006-08-25
forum: Desktop Environments
---

### Post by wbdown2008 on 2006-08-25
Hi,

I'm new to Ubuntu and would like some help.

I'm trying to setup an MP3 alarm clock on Ubuntu Dapper using Cron. More info can be found on these two websites: [http://www.federicopistono.org/index.php?mod=Tutorial/Alarm_Clock]("http://www.federicopistono.org/index.php?mod=Tutorial/Alarm_Clock")
[http://grimthing.com/archives/2004/01/23/cron-mp3-alarm-clock/]("http://grimthing.com/archives/2004/01/23/cron-mp3-alarm-clock/")

I went through both websites to figure out how to set it up. The problem I had was with the different script ideas for alarm.

This is the first script I used for alarm:

> #!/bin/sh
mplayer -really-quiet -shuffle -playlist /home/grim/.playlist

it ran very smoothly, but didn't really like the fact that it just ran in the background without anyway to turn it off without going to System Monitor and ending the process there.

However, I found this script on the other website:

> #!/bin/sh

# Uncomment if you want to use amaroK
#/usr/bin/dcop /usr/bin/amarok player play

#Comment if you do not want to use Mplayer
/usr/bin/X11/xterm -display :0 -bg black -fg white \
-e /usr/local/bin/mplayer -shuffle -playlist ~/.playlist

# Eterm solution#/usr/bin/Eterm -0 -e /usr/local/bin/mplayer \
# -shuffle -playlist ~/.playlist


This script is the same as the one above it, but would allow mplayer to run in a xterm window. This is where I ran into problems. Apparently Cron won't start the xterm window when I run this script.

Is there anyway to get Cron to run mplayer in a terminal? Any help is apprciated. Thanks!

WBD

---

### Post by Anduu on 2006-08-25
Well I just tested it out and it opens an xterm window for me...

Did you remember to make your script excecutable?

---

### Post by wbdown2008 on 2006-08-26
> **Anduu said:**
> Well I just tested it out and it opens an xterm window for me...

Did you remember to make your script excecutable?

I ran chmod on the script, but still nothing happened.

---

