---
title: "Starting an GUI Desktop application from a cron job"
date: 2006-10-10
forum: Desktop Environments
---

### Post by crudolphy on 2006-10-10
I have a simple script that I run to start up Firefox with 3 tabs to different web sites as follows:

#!/bin/sh

#MORNING.SH

#USER VARIABLES

WEB1="traffic.houstontranstar.org/layers/";
WEB2="traffic.houstontranstar.org/routebuilder/routebuilder.aspx?ID=090-091-092-093-094-095-096-134";
WEB3="www.srh.noaa.gov/forecast/MapClick.php?CityName=Spring&state=TX&site=HGX";
FIREFOX="/usr/lib/firefox/firefox";

#START FIREFOX AND PASS THE URL'S TO THE BROWSER WHICH WILL OPEN IN TABS

$FIREFOX http://$WEB1 $WEB2 $WEB3 & 

I can open gnome terminal and run this script from the command line and Firefox starts up and opens three tabs to the selected web sites, just like I want it to.  I have even created a launcher for the script which works just fine.  I click on the icon and up pops Firefox and it loads the pages perfect.  If I go to a tty session(CTLALT F1 thru F6) and run the script it fails as it can't load GTK in a tty session there is no X server running in this environment.

My problem is that I want to run the script automatically at 6:55am Monday thru Friday morning.  If I put it in a cron job it fails (Firefox doesn't start, no web pages).   I suspect this fails in the cron job for the same reason that it fails from a tty session, however there has to be a way to be a way to do this.

Can anyone suggest where my error is?

Chuck

---

### Post by TheWizzard on 2006-10-11
how did you configure cron to run this script? 
if you edited the files in /etc, the cron jobbs are owned by root. 
i would not recommend opening web-pages as root. this is a serious security tread! use scheduling software for jobs like this.

---

### Post by ayoli on 2006-10-11
you have to set display environement variable to launch a gui app from a cronjob, like this:
```
10 10 * * * DISPLAY=:0 /path/to/your/script
```

---

### Post by crudolphy on 2006-10-11
Thanks for your replies.  I did not edit the cron files in /etc.  I created a cron that runs under my user name with the crontab -e command.  It looks as follows:

55 6 * * 1,2,3,4,5 DISPLAY=:0.0 sh /home/chuck/morning.sh

Your instructions on the "DISPLAY" variable did the trick.  Thanks a lot!  I tested with a different time and up popped my websites.  I have changed the script as follows:

#!/bin/sh

#MORNING.SH

#USER VARIABLES

WEB1="traffic.houstontranstar.org/layers/";
WEB2="traffic.houstontranstar.org/routebuilder/routebuilder.aspx?ID=090-091-092-093-094-095-096-134";
WEB3="www.srh.noaa.gov/forecast/MapClick.php?CityName=Spring&state=TX&site=HGX";
SUCCESS="/usr/share/sounds/k3b_success1.wav";
FAIL="/usr/share/sounds/k3b_error1.wav";
FIREFOX="/usr/lib/firefox/firefox";

#START FIREFOX AND PASS THE URL'S TO THE BROWSER WHICH WILL OPEN IN TABS

$FIREFOX http://$WEB1 $WEB2 $WEB3 & 

sleep 5;

ps -C firefox-bin -o state= >/dev/null

if [ $? = 0 ]
 then
	cat $SUCCESS > /dev/dsp
	exit
 else
	cat $FAIL > /dev/dsp
	exit
 fi;

Now dependent upon the success or failure of starting firefox I get an audible sign kind of like an alarm clock.  (Will tell me I need to get out the door to work.);) 

Thanks for your help.

Chuck

---

