---
title: "[SOLVED] Indesk Picture"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by dedtr9 on 2008-01-08
I have satellite internet, and on the admin panel there is an image depicting the current usage out of total for that month. I have the url for the image, and it updates every so often. I keep going over the limit and have the internet cut off, so i was wondering how i could get the image embedded into the desktop or something.
It would sits on my background and update every hour or something similar. The way with lowest possess usage would be best, but whatever works is fine.

---

### Post by heimo on 2008-01-08
A short bash script using wget or curl, scheduled to run periodically using cron should do it. You could check examples of how people get their daily Dilbert or similar stuff updated / ripped automatically. Basically, you first load the web page to memory using wget, extract url, download that image and save it as your desktop image (may need some trick to get actually refreshed/changed on fly).

---

### Post by dedtr9 on 2008-01-08
Ok, i'll look into how to write a script for it. Is there any way to get it to take up part of my background: have it layered over my background in a corner somewhere?

---

### Post by dedtr9 on 2008-01-10
I got it to overlay the image with this command:
convert linux.jpg -page +0+980 wbUsage.png -background none -flatten out.jpg
where linux.jpg is my background, but i cant seem to get it automatically with any command. wget, and curl seem to have problems doing it. 

Here is a link to the blank graph that i am trying to get downloaded
[https://admintool.trueband.net/cgi-bin/wbUsage.cgi?username=&mode=30](https://admintool.trueband.net/cgi-bin/wbUsage.cgi?username=&mode=30)

Edit: I had to put the url in quotes, the & was messing it up

here is the script i have to get the picure, overlay it with my original bg, then set it:

```

#!/bin/bash
cd /home/iuvat/Desktop/bg
wget -q --no-check-certificate 'https://admintool.trueband.net/cgi-bin/wbUsage.cgi?username=username@gotsky.com&mode=30'
mv -f 'wbUsage.cgi?username=usernamel@gotsky.com&mode=30' 'wbUsage.png'
convert linux.jpg -page +0+980 wbUsage.png -background none -flatten out.jpg
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/iuvat/Desktop/bg/out.jpg"
```

It's my first official script, so its not to too great, but it seems to work.

---

