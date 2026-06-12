---
title: "weather map as desktop background (gnome)"
date: 2010-07-07
forum: Desktop Environments
---

### Post by wayover13 on 2010-07-07
I wanted to use a regularly- and frequently-updating weather map as my desktop background (extreme desktop tweakers can stop reading here: yes, I'm committing the unspeakable act of using a 640x480 image as the background for my 1280x1024 desktop. What can I say? I'm a pragmatic kinda guy . . .). I came up with the following solution for doing this, but wanted to post here to see if someone else might suggest something more elegant and/or superior.

First, I created an extremely simplistic bash script that downloads the weather map image (640x480 a gif) and writes it to a file in my home directory called wmap-bkgrnd.gif. It's only two lines, as follows: > #!/bin/sh
wget -O /home/user/wmap-bkgrnd.gif [http://rest-of-URL-for-weather-map.gif](http://rest-of-URL-for-weather-map.gif) I made the script executable and called it wmap-get (I made a symlink to it in /usr/bin so it would be available system-wide, too). Next, I edited my user's crontab file and put in the entry > 0-59/10 * * * * wmap-get So now cron downloads the image every 10 minutes and writes it to the wmap-bkgrnd.gif file in my user's home directory. Finally, I right-clicked on the gnome desktop and selected "change background," selecting that image as my desktop background.

It works, and gives the desired effect. I now have a weather map that updates every 10 minutes as my desktop background.

So, my questions. Is there a simpler/better way to accomplish this task? I have to say I have nothing against higher-resolution images and would use one if I could find something suitable. But so far, in the way of frequently-updated maps, I've only been able to find this low-resolution one.

Any suggestions for tweaks and/or improvements will be appreciated.

Thanks,
James

---

### Post by d3v1150m471c on 2010-07-07
you may want to look into a program called xwinwrap... at least i think it's called xwinwrap. it allows you to do a lot of awesome desktop stuff.

---

### Post by wayover13 on 2010-07-08
I found I had to make a correction to my crontab file. I changed > 0-59/10 * * * * wmap-get to > */10 * * * * wmap-get after I noted that the map was being updated more frequently than I expected, i.e., more often than every 10 minutes. The most suitable map I've located so far can be found at [http://radar.weather.gov](http://radar.weather.gov) (U.S. location), by the way.

James

---

### Post by wayover13 on 2010-07-08
In a new iteration of this solution, I found a high-resolution (3400x1600) weather map--though it's one of the entire U.S., rather than just my region (upper midwest). It can be found at [http://radar.weather.gov/ridge/Conus/RadarImg/latest.gif](http://radar.weather.gov/ridge/Conus/RadarImg/latest.gif) . As usual, imagemagick comes to the rescue.

I changed the URL in my script accordingly and appended > && mogrify -crop 1280x1024+1400+100 /home/user/wmap-bkgrnd.gif afterward. And, voila! That bit causes the image to be cropped to 1280x1024, centered on my area of the country. Looks and works fine so far (see [http://www.linuxtutorialblog.com/post/cropping-multiple-images-the-same-way-short-tutorial](http://www.linuxtutorialblog.com/post/cropping-multiple-images-the-same-way-short-tutorial) for some tips on imagemagick and use of the mogrify command).

Ok, if no one has any ideas for improving on what I've done, at least maybe someone else who wants to do something like this can benefit from this thread.

James

---

### Post by wayover13 on 2011-07-19
Here's the latest iteration of this project. I should mention up front that I'm migrating away from gnome, so I'm not sure how relevant what follows will be for gnome users. The reason, as I understand it, that this may not work so well for gnome is that gnome takes control of the root window, while the solution I've now come up with relies on a program that puts a picture (gif) on the root window. What I can say is that the solution works under openbox, the WM I'm now testing as my possible post-gnome WM. It would probably work on many other, less demanding WM's as well.

I do essentially the same routine of downloading a national weather map every 10 minutes and using imagemagick to crop it to my desktop's size and to my area of the country. The difference is that I'm using feh to put the image thus downloaded and cropped on the desktop's background.

I created a simple script that takes care of the downloading, the cropping, and the running of feh to put the image on the desktop background. I cause that script to run every 10 minutes using cron (crontab -e). Probably it will be simplest if I just post my script here: ```
#!/bin/sh
wget -O /home/myuser/wmap-hi_res.gif http://radar.weather.gov/ridge/Conus/RadarImg/latest.gif && mogrify -crop 1280x1024+1400+100 /home/myuser/wmap-hi_res.gif && feh --bg-center /home/myuser/wmap-hi_res.gif > /dev/null 2>&1
```

I should also point out that the crontab entry needs to have something prepended to the script's name. I was initially able to make the script work fine from the command line, but it would not work as a cron job. Some further research revealed that it was not working because I needed to tell cron to which display the script needed to be applied (:0.0). The crontab entry, then, looks like this ```
*/10 * * * * DISPLAY=:0.0 wmap-get
```
(solution found on the arch forums at [https://bbs.archlinux.org/viewtopic.php?pid=415591](https://bbs.archlinux.org/viewtopic.php?pid=415591) ) Hope this may be of benefit to others.

James

---

