---
title: "Autoupdate URL image as desktop background"
date: 2007-08-18
forum: Desktop Environments
---

### Post by ambrosa on 2007-08-18
Ubuntu 7.04 (Gnome)

I'd like to use this image *[http://image.weather.com/images/sat/italy_sat_720x486.jpg](http://image.weather.com/images/sat/italy_sat_720x486.jpg)* as desktop backgorund. This image is changed in remote server about every hour (but the name doesn't change).

So I've do a little cron shell script for downloading the image every 30 min and put in /usr/local/backgorunds/sat
-------------
#!/bin/sh
wget -o /dev/null -q -O /usr/share/backgrounds/sat/italy_sat.jpg -t 5 [http://image.weather.com/images/sat/italy_sat_720x486.jpg](http://image.weather.com/images/sat/italy_sat_720x486.jpg)
-----------
It works fine.

Now there is the problem to use and to update periodically the image downloaded as desktop background.
I've installed the package **wallpaper-tray** but it doesn't work right. I've configured with only one directory list ( /usr/local/backgorunds/sat ): it load the image ONCE but don't reload it anymore.
I've tried to check "Timed wallpaper Change" but it doesn't work.
Well, I can forget "wallpaper-tray" package. 

How can I solve this ?
I can set desktop backround to /usr/share/backgrounds/sat/italy_sat.jpg but how can I instruct Gnome to reload desktop beckgorund every 30 min. ? If there is such command, I can put in another (or the same above) cron shell script..... but I don't know.
Someone can help me ?

---

### Post by ambrosa on 2007-08-21
I've found a simple solution: use gconftool

I've removed wallpaper_tray package then I've created this script run  as local user using cron (*crontab -e*) :
-------------get_sat_image.sh------------
#!/bin/sh
# delete original image
rm -f ~/MyImages/italy_sat.jpg
# get image from weather.com and save in my HOME
wget -o /dev/null -q -O ~/MyImages/italy_sat.jpg -t 5  [http://image.weather.com/images/sat/italy_sat_720x486.jpg](http://image.weather.com/images/sat/italy_sat_720x486.jpg)
# reset background with a non-existent image
# if you don't use this, then next line will not update the wallpaper
gconftool -s -t string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
# load new desktop background image
gconftool -s -t string /desktop/gnome/background/picture_filename ~/MyImages/italy_sat.jpg
--------------------------

I run this script every 15 min.

---

### Post by wwood on 2007-10-17
Hi,

Thanks for posting your answer. I modified it below, so that instead of taking an image as a satellite image, I used a random image from the LiveJournal blog site. There is probably a more efficient way to do this, but the site 

[http://www.lostsheep.com/lj.php](http://www.lostsheep.com/lj.php)

Actually lists random images. I've just downloaded that HTML, parsed out the image url, and then downloaded that image. Here's the script:

autoupload_wallpaper.sh
```
#!/bin/bash

wget -o /dev/null -q -O /tmp/wallpaper.html http://www.lostsheep.com/lj.php 2>/dev/null
wget -o /dev/null -q -O /tmp/wallpaper `grep "img src" /tmp/wallpaper.html |head -n1 |sed -e "s/.*img src=.\(.*\). alt.*/\1/"` 2>/dev/null

# testing
#eog /tmp/wallpaper &

# reset background with a non-existent image
# if you don't use this, then next line will not update the wallpaper
gconftool -s -t string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
# load new desktop background image
gconftool -s -t string /desktop/gnome/background/picture_filename /tmp/wallpaper
```

And then I modified my crontab to get a new pic every minute.

Hope someone finds this and finds it useful.

ben

---

