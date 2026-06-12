---
title: "wallpaper from cron job"
date: 2014-04-26
forum: Desktop Environments
---

### Post by Impavidus on 2014-04-26
Hey all,

For some years I have used a cron job on my Xubuntu laptop (and previous machines) running a script to download new wallpapers for my screen every hour (images from a weather satellite). Just replacing the file doesn't work as the image will not be reloaded until the next time I log in, but when the path to the file is changed using xfconf-query and the DBUS_SESSION_BUS_ADDRESS environment variable is fetched from the file ~/.dbus/session-bus/<session> it worked on Precise. But not so well on Trusty. On Precise I used the code```
for session in $HOME/.dbus/session-bus/*; do
    echo using session $session >> $logfile
    export $(grep ^DBUS_SESSION_BUS_ADDRESS $HOME/.dbus/session-bus/$session)
    echo address >> $logfile
    echo $DBUS_SESSION_BUS_ADDRESS >> $logfile
    xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path \
        -s $HOME/images/image2.jpg 2>> $logfile
    echo exit status of xfconf-query $? >> $logfile
done
```Occasionally bad cleanup caused multiple session files to be present, but the bad ones were ignored by using the for loop.
On Trusty however the wallpaper is not changed. I already found that I had more success when changing the property to set with xfconf-query to /backdrop/screen0/monitorLVDS1/workspace0/last-image, as that is the property apparently changed by the GUI wallpaper selector, and it seemed to have worked on a few occasions, but not today. The logfile gives the following output (translating from dutch):```
using session 8b8f9894c1ebe53111da3fb25352ab83-0
address
unix:abstract=/tmp/dbus-rPzq6eqwgi,guid=f199ea009dd5e6ab98452506535a554c
Could not initialise libconf: Failed to connect to socket /tmp/dbus-rPzq6eqwgi: Connection refused
exit status of xfconf-query 1
```

Ideally I'd like a command to force the system to reload the image file (a jpeg) whenever the script determines that a new image has been downloaded. If that can't be done – and I didn't manage to do that on Precise – I can use a workaround by alternating between two file names. I plan on modifying the script a bit to do something else during the  night when no visible light images are availabe, so this gets a little  too complicated to do with simple wallpaper switchers. I run the same script at login.

Thanks.

---

### Post by Impavidus on 2014-05-07
Solved it myself.

The original version of the script used gconftool, a different linux distro broke the script so I had to use gconftool-2, next switching to xfce forced me to use xfconf-query fetching the DBUS_SESSION_BUS_ADDRESS from ~/.dbus/session-bus/<session>, which no longer exists. The latest incarnation of the wallpaper switcher now finds the PID of xfce4-session using ps and uses that to get the environment variables for that process from /proc. Then I can set the dbus address from there. At the same time I had to change the property that is set by xfconf-query. To make sure the new background gets loaded I first set the path to an empty string. Skipping some error handlers:```
#!/bin/bash
#Set and clear the log file
logfile=$HOME/.wallpaper.log
: > $logfile
#Fetch the PID
pid=$(ps -C xfce4-session -o pid=)
#Hack to remove the leading space. Maybe not so nice, but it works.
pid=$(echo $pid)
#Get the environment variable from /proc
export $(grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ)
#Use wget to download the image
wget --no-verbose --append-output=$logfile --tries=3 --waitretry=5 --directory-prefix=$HOME/Pictures \
    --no-directories --timestamping http://oiswww.eumetsat.org/IPPS/html/latestImages/EUMETSAT_MSG_RGB-12-12-9i-segment4.jpg
#Set the wallpaper to an empty path
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitorLVDS1/workspace0/last-image -s "" 2>> $logfile
#Reload the wallpaper
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitorLVDS1/workspace0/last-image \
    -s $HOME/Pictures/EUMETSAT_MSG_RGB-12-12-9i-segment4.jpg 2>> $logfile
```
Now let's see when will be be the next time this breaks.

---

