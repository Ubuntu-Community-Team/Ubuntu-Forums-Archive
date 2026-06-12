---
title: "cron bash and desktop: HELP please!"
date: 2009-01-04
forum: General Help
---

### Post by dblslash on 2009-01-04
I'm kind of new to linux, and I really need help on this particular problem. 
I wrote a script to change my background wallpaper, and it works perfectly when invoked from a shell. I added the script's pathname to the variable PATH and can successfully call it by its name (w/o typing the full path). For example, at the prompt this command 
*desktop-changer*
will successfully change my desktop background.

Next, I tested cron with a very simple command, and it worked perfectly. In particular, I uploaded this file (called cron-dc)
** * * * * echo hi > log.txt*
to crontab using the command
*crontab -u dblslash cron-dc*

Indeed, every minute I would see log.txt created in my HOME directory. So, now I have a working cron and a working script, but when I put the 2 together, they don't work.

I followed the same procedure to upload my wallpaper-changing cron job.My crontab entry for changing the background is
** * * * * desktop-changer*
 I also tried the following variations, but none worked
** * * * * /home/dblslash/bin/desktop-changer* (full path specified)
** * * * * /bin/bash /home/dblslash/bin/desktop-changer* (explicitly calling bash to execute the script)

I spent God knows how many hours searching on the Internet, this forum, and books to fix this problem to no avail. I understand this it has been discussed before here and some other sites, but their solutions didn't work for me. Any suggestions would be greatly appreciated.

---

### Post by furry_freak on 2009-01-04
Thats funny, I've been having problems with cron, Ive been trying to execute a script and it wouldnt work, when I saw yuor post I tried "* * * * * echo !!! >> log.txt" it worked...

i'll try "* * * * * /bin/sh script.sh" n see if that works. EDIT: nope dont work...

---

### Post by Stelaninja on 2009-04-07
I have the very same problem and none of the solutions I've found in any forum works. Can anyone solve this. I've tried to use the /etc/crontab file as well. But no, it doesn't work. Now I've put the cronfile in /etc/cron.d but that doesn't make it any better. As you can see in the syslog cron runs the script but nothing seems to happen.. =( Help, please!

/var/log/syslog:

```

Apr  7 13:39:01 nibiru /USR/SBIN/CRON[30120]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  7 13:40:01 nibiru /USR/SBIN/CRON[30336]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:40:01 nibiru /USR/SBIN/CRON[30338]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  7 13:40:10 nibiru NetworkManager: <debug> [1239104410.002658] periodic_update(): Roamed from BSSID 00:22:B0:A4:D4:0A (DeathStar) to (none) ((none)) 
Apr  7 13:40:16 nibiru NetworkManager: <debug> [1239104416.003159] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:B0:A4:D4:0A (DeathStar) 
Apr  7 13:41:01 nibiru /USR/SBIN/CRON[30658]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:42:01 nibiru /USR/SBIN/CRON[30782]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:42:10 nibiru NetworkManager: <debug> [1239104530.002316] periodic_update(): Roamed from BSSID 00:22:B0:A4:D4:0A (DeathStar) to (none) ((none)) 
Apr  7 13:42:16 nibiru NetworkManager: <debug> [1239104536.004156] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:B0:A4:D4:0A (DeathStar) 
Apr  7 13:43:01 nibiru /USR/SBIN/CRON[30905]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:44:01 nibiru /USR/SBIN/CRON[31031]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:44:09 nibiru NetworkManager: <debug> [1239104650.002522] periodic_update(): Roamed from BSSID 00:22:B0:A4:D4:0A (DeathStar) to (none) ((none)) 
Apr  7 13:44:16 nibiru NetworkManager: <debug> [1239104656.002951] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:B0:A4:D4:0A (DeathStar) 
Apr  7 13:45:02 nibiru /USR/SBIN/CRON[31155]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:46:01 nibiru /USR/SBIN/CRON[31278]: (stefan) CMD (/home/stefan/changewall)
Apr  7 13:46:10 nibiru NetworkManager: <debug> [1239104770.003276] periodic_update(): Roamed from BSSID 00:22:B0:A4:D4:0A (DeathStar) to (none) ((none)) 

```

/home/stefan/changewall:

```

#!/bin/bash
HOUR=$(date +%H)
case $HOUR in
21|22|23|00|01|02|03|04|05|06)
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/stefan/Bilder/Backgrounds/lake_sky.jpg
;;
12|13|14|15|16|17|18|19|20)
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/stefan/Bilder/Backgrounds/iceland_road.jpg
;;
09|10|11)
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/stefan/Bilder/Backgrounds/beach_horiz.jpg
;;
*)
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/stefan/Bilder/Backgrounds/beach_chairs.jpg
;;
esac

```

/etc/cron.d/change_wall:

```

PATH=/bin:/usr/bin:/usr/local/bin:/home/stefan

* * * * * stefan /home/stefan/changewall

```

---

### Post by tnprivacy on 2009-04-11
> **Stelaninja said:**
> I have the very same problem and none of the solutions I've found in any forum works. Can anyone solve this. I've tried to use the /etc/crontab file as well. But no, it doesn't work. Now I've put the cronfile in /etc/cron.d but that doesn't make it any better. As you can see in the syslog cron runs the script but nothing seems to happen.. =( Help, please!

[/CODE]

This is a problem I have experienced with Ubuntu for quite a while. User cron will happily execute logger, echo etc., but refuses to run any code that tries to change the gnome desktop background, whether it is gconftool (from bash) or the gconf module in python.

It works in opensuse which I have on my notebook so it seems to be a Ubuntu specific problem (I have not checked Debian to see if the mothership has the same problem).

My quick and dirty solution, since I do not have to time to fully trouble shoot the problem is to just put the changer script in another wrapper script with an infinite loop. Example below (change every 15 minutes (15*60=900), adjust to requirements).

#!/bin/bash
until [ 6 -eq 9 ]; do /path_to_script/changer_script; sleep 900; done

then just add it to your startup programs or launch it in the background with &

Of coarse if anyone has found the solution to running it from cron, I would love to hear.

---

