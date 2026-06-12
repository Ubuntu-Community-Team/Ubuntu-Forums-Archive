---
title: "crontab doesn't execute python script right"
date: 2009-04-29
forum: General Help
---

### Post by msegmx on 2009-04-29
/etc/crontab :

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#0,5,10,15,20,25,26,30,35,40,45,50,55 * * * * mserkan python /home/mserkan/.myscripts/randomwallpaper.py
* * * * * mserkan python /home/mserkan/.myscripts/randomwallpaper.py >/home/mserkan/.myscripts/myscript.log 2>&1
#


/home/mserkan/.myscripts/randomwallpapers.py :

#!/usr/bin/env python

from os import listdir, system
from random import sample

#get list of files in /mnt/Work/resources/visuals/wallpapers/
fileList = listdir("/mnt/Work/resources/visuals/wallpapers/")
#randomly choose one
theChosenOne = sample(fileList, 1)
#set wallpaper
system('gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/mnt/Work/resources/visuals/wallpapers/' + str(theChosenOne[0]) + '"')
#scale wallpaper
system('gconftool-2 --type string --set /desktop/gnome/background/picture_options "zoom"')

here's my ls -l output : 

[email]mserkan@UbuntuPC:~/.myscri[/email]pts$ ls -l
total 8
-rw-r--r-- 1 mserkan mserkan   0 2009-04-29 18:21 myscript.log
-rwxr-xr-x 1 mserkan mserkan 539 2009-04-29 17:50 randomwallpaper.py
-rw-r--r-- 1 mserkan mserkan 593 2009-04-29 17:49 randomwallpaper.py~
[email]mserkan@UbuntuPC:~/.myscri[/email]pts$ 



In a terminal when I run  : 
[email]mserkan@UbuntuPC:~/.myscri[/email]pts$ python randomwallpaper.py 
it works, the wallpaper changes immediately.
when I delete the myscript.log file, it is created every minute again, hence I guess the python script is being run every minute. the created log file is empty.

this script worked in Ubuntu 8.04 through a crontab entry
but I couldn't get it work through a crontab entry in Ubuntu 9.04.

can anybody help me ?

---

### Post by msegmx on 2009-04-29
bump

---

### Post by xeddog on 2009-05-01
I have read in another thread that when executing python scripts in cron you need to add:

DISPLAY=:0.0

as the first line in your crontab.  I was having trouble with a python script that displays weather information on my desktop until I added the above to my crontab and now it works.

xeddog 

P.S.  This is apparently either a bug or change made in Jaunty.

---

