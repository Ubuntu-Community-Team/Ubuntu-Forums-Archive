---
title: "Facebook Indicator Applet"
date: 2011-05-27
forum: Desktop Environments
---

### Post by raynesax on 2011-05-27
Hello,I'm trying to make an applet for ubuntu 11.04 which can display my facebook's new requests,messages and notifications.I want to employ python for the purpose.I've created a basic interface of the applet(you can have a look at it as i attached a pic here).But now i'm not getting any idea about how to proceed further and how i can fetch new notifications etc from fb profile.Also what technology can i use along with python.

---

### Post by kostkon on 2011-05-27
You could start with the [pyfacebook library]("http://packages.ubuntu.com/natty/python-facebook").

Also, there is facebook's own [python SDK]("https://github.com/facebook/python-sdk/").

Hope that helps.

---

### Post by wildmanne39 on 2011-05-28
> **raynesax said:**
> Hello,I'm trying to make an applet for ubuntu 11.04 which can display my facebook's new requests,messages and notifications.I want to employ python for the purpose.I've created a basic interface of the applet(you can have a look at it as i attached a pic here).But now i'm not getting any idea about how to proceed further and how i can fetch new notifications etc from fb profile.Also what technology can i use along with python.
Hi, I have conky setup to get face book notifications, the only part I have not got to work is seeing pictures from face book on my desktop.
```
#position
gap_x 10
gap_y 25
alignment bottom_left

#behaviour
# Update interval in seconds
update_interval 1

#colour
default_color  ffffff
default_shade_color 000000
own_window_colour 555555
default_outline_color 01040d
draw_outline no

#font
use_xft yes
xftfont DejaVu Sans:pixelsize=10

#to prevent window from moving
#use_spacer no               
minimum_size  300 250
#mpd
mpd_host localhost
mpd_port 6600     

TEXT
${offset -5}${Color Blue}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}FaceBook Notifications${font}  ${hr}${color1}

${rss http://www.facebook.com/feeds/notifications.php?id=censored&viewer=censored&key=censored&format=rss20  1 item_titles 10}

${offset -5}${Color Blue}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Photos${font}  ${hr 2}${color1}

Attached Thumbnails
Click image for larger version Name: 

```

---

### Post by kid1000002000 on 2012-11-19
just curious what became of this. I would be interested!

---

### Post by lisati on 2012-11-19
> **kid1000002000 said:**
> just curious what became of this. I would be interested!

A lot can change in the software world in a year. If a thread hasn't had a response in over a year, it would be appreciated if you start a new thread, with a link back to the original thread.

---

