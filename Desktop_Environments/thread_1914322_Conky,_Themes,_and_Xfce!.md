---
title: "Conky, Themes, and Xfce!"
date: 2012-01-24
forum: Desktop Environments
---

### Post by mang0 on 2012-01-24
Hey all. 

I'm using the Xubuntu session on Ubuntu 11.04 (I installed xfce and xubuntu-desktop). It's version 4.8. However, I'd like to use a different theme to the defult one. When I looked on [http://www.xfce-look.org/](http://www.xfce-look.org/), I can see loads of nice themes, but I can't seem to get them to work? Is this a problem to do with the GTK version or something?

I'm also trying (and failing fantastically!) to get conky working. I've managed to get one config to work, but it's not the sort of thing I'd like - I'd like a clock, date, music player controls (stop, pause, next, previous, name of track), RSS reader, and CPU/RAM/Disk space usage. I'm really failing to find a config that I like though :/ I've check in [this thread]("http://ubuntuforums.org/showthread.php?t=281865"), but I've not found anything I like.

Any help on either of these issues greatly appreciated!
Thanks.

---

### Post by mang0 on 2012-01-24
Someone? :'(

---

### Post by nothingspecial on 2012-01-24
Please do not bump your thread more frequently than every 24 hours or so.

---

### Post by mang0 on 2012-01-24
Sorry, I've not been on the forums for a while, forgot that rule ;)

EDIT: Uh, this doesn't count as a bump does it? :/

---

### Post by Toz on 2012-01-24
> **mang0 said:**
> Hey all. 

I'm using the Xubuntu session on Ubuntu 11.04 (I installed xfce and xubuntu-desktop). It's version 4.8. However, I'd like to use a different theme to the defult one. When I looked on [http://www.xfce-look.org/](http://www.xfce-look.org/), I can see loads of nice themes, but I can't seem to get them to work? Is this a problem to do with the GTK version or something?
What do you mean by "can't seem to get them to work". What is happening when you try? With xfce, you need to make changes in two places, the apperance applet (gtk theme) and window manager applet (xfwm theme). Both applets are located under Settings in Settings Manager. Make sure you extract the theme files to ~/.themes (user-specific) or /usr/share/themes (system-wide).

> I'm also trying (and failing fantastically!) to get conky working. I've managed to get one config to work, but it's not the sort of thing I'd like - I'd like a clock, date, music player controls (stop, pause, next, previous, name of track), RSS reader, and CPU/RAM/Disk space usage. I'm really failing to find a config that I like though :/ I've check in [this thread]("http://ubuntuforums.org/showthread.php?t=281865"), but I've not found anything I like.
Conky is the type of utility that requires you to spend some time understanding how it works. The more you put into it, the more you will get out of it. There is nothing wrong though, with locating a configuration that you like and tailoring it to your needs. Other good resources of conky configurations include:
- [http://conky.sourceforge.net/]("http://conky.sourceforge.net/")
- [http://wiki.conky.be/index.php?title=Conky_Wiki]("http://wiki.conky.be/index.php?title=Conky_Wiki")
- [http://blog.conky.be/]("http://blog.conky.be/")
- [http://www.techdrivein.com/2010/12/13-breathtaking-conky-configurations.html]("http://www.techdrivein.com/2010/12/13-breathtaking-conky-configurations.html")

---

### Post by akshay.chandorkar1 on 2012-01-24
Hay toz....i am Akshay from india....i am trying to configure conky.....my .conkyrc says following
............................................................................................................................................................................
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844



TEXT
 ${color D3DADF}${font OpenLogos:size=45} u t
${font weather:size=82}${color C9CFD4}${execi 600 ~/scripts/conditions.sh}${color 265276}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${color 4EA9F3}${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${color}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color 014A7F}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py email@domain password}

   ${color 014A7F}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${color 014A7F}${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

.....................................................................................................................................................................

I got this from the website

[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/#idc-cover](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/#idc-cover)

and is installed as the installation giuld says
.......................................................................................................................................................................

When running the conky from the terminal it says

akshay@akshay-desk:~$ conky
Conky: /home/akshay/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (e00023) is subwindow of root window (b0)
Conky: window type - override
Conky: drawing to created window (0x3400001)
Conky: drawing to double buffer
/home/akshay/scripts/pogodynka.sh: 50: w3m: not found
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/akshay/scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 663, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 632, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 659, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 694, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 776, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 681, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 379, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0xb722996c>)
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
.
.
.
.

and it stops here and nothing happens..............................................................................................................

---

### Post by Toz on 2012-01-24
> **akshay.chandorkar1 said:**
> 
akshay@akshay-desk:~$ conky
Conky: /home/akshay/.conkyrc: 14: no such configuration: 'border_margin'
border_margin is no longer a valid variable. Use either border_inner_margin or border_outer_margin. See: [http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")
> Conky: desktop window (e00023) is subwindow of root window (b0)
Conky: window type - override
Conky: drawing to created window (0x3400001)
Conky: drawing to double buffer
/home/akshay/scripts/pogodynka.sh: 50: w3m: not found
You need to install w3m:
```
sudo apt-get install w3m
```
> Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
BAT0 is not your battery. You need to replace BAT0 in the script with your battery name. To find it, try:
```
ls /sys/class/power_supply
```
> Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Once you get your battery name, replace "/proc/acpi/battery/BAT0/state" in the script with:
```
/proc/acpi/battery/<battery_name>/state
```
...where <battery_name> is the name of your battery
> Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/akshay/scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 663, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 632, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 659, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 694, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 776, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 681, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 379, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0xb722996c>)
Did you install python-feedparser?
```
sudo apt-get install python-feedparser
```
> Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Once you fix the battery name issue, these will disappear.
> 
.
.
.
.

and it stops here and nothing happens..............................................................................................................
Nothing? Try fixing the above and see if it helps.

---

### Post by mang0 on 2012-01-24
> **Toz said:**
> What do you mean by "can't seem to get them to work". What is happening when you try? With xfce, you need to make changes in two places, the apperance applet (gtk theme) and window manager applet (xfwm theme). Both applets are located under Settings in Settings Manager. Make sure you extract the theme files to ~/.themes (user-specific) or /usr/share/themes (system-wide).

Conky is the type of utility that requires you to spend some time understanding how it works. The more you put into it, the more you will get out of it. There is nothing wrong though, with locating a configuration that you like and tailoring it to your needs. Other good resources of conky configurations include:
- [http://conky.sourceforge.net/](http://conky.sourceforge.net/)
- [http://wiki.conky.be/index.php?title=Conky_Wiki](http://wiki.conky.be/index.php?title=Conky_Wiki)
- [http://blog.conky.be/](http://blog.conky.be/)
- [http://www.techdrivein.com/2010/12/13-breathtaking-conky-configurations.html](http://www.techdrivein.com/2010/12/13-breathtaking-conky-configurations.html)

Ah, okay, I was doing some stuff wrong with themes then. Thanks. As to conky, I appreciate the links, a couple of them I didn't know about. Thankyou.

---

### Post by akshay.chandorkar1 on 2012-01-27
Hay Toz.....I think the problem was with the borde margin only becoz i have w3m installed....Now the conky is working fine but the gmail feed is not working.......I also removed the battery bar from conky as i am using desktop......This is the output from my terminal...........
.........................................................................................................................................................................................


akshay@akshay-desk:~$ conky
Conky: desktop window (e00023) is subwindow of root window (b0)
Conky: window type - desktop
Conky: drawing to created window (0x2200001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 22, in <module>
    maxlen = sys.argv[3]
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 22, in <module>
    maxlen = sys.argv[3]
IndexError: list index out of range
.
.
.
.
and it stops here ..........................................

And about the email address and password......that was foolish of me......i changed it the moment i posted. But thank you for reminding me anyway.....

---

### Post by Toz on 2012-01-27
Try changing the line:
> ${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py email@domain password}

by adding quotes around your username and password. Also, there needs to be a value at the end (the website shows 3). Something like this:

```
${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py "email@domain" "password" 3}
```

Note: This script worked for me a couple of days ago but not today. I'm getting a "IOError: ('http error', 401, 'Unauthorized'" error.

---

### Post by akshay.chandorkar1 on 2012-01-27
Not working..........................
The terminal output is as follows...............
.............................................................................................................................................................................................

akshay@akshay-desk:~$ conky
Conky: desktop window (e00024) is subwindow of root window (b0)
Conky: window type - normal
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/akshay/scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 663, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 632, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 659, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 694, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 776, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 681, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 379, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0xb71c196c>)

---

### Post by Toz on 2012-01-27
I get the same now:
> IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0xb71c196c>)

Gmail is not authorizing it. Perhaps something has changed with gmail?

---

### Post by Toz on 2012-01-27
Try this script instead (it worked for me just now):
```

import os
 
#Enter your domain, username and password below within double quotes
# eg. domain="yourdomain.com", username="username" and password="password"
domain="gmail.com"
username="username"
password="password"
com="wget -q -O - https://mail.google.com/a/"+domain+"/feed/atom --http-user="+username+"@"+domain+" --http-password="+password+" --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=msg.find("<fullcount>")
index2=msg.find("</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"

```
...make sure you change:
- domain (usually gmail.com)
- username
- password

Source: [https://wiki.archlinux.org/index.php/Conky#Display_number_of_new_emails_.28Gmail.29]("https://wiki.archlinux.org/index.php/Conky#Display_number_of_new_emails_.28Gmail.29")

---

### Post by ohnonot on 2012-02-11
i had some problems myself with getting gtk and xfwm themes to work.
i had them all downloaded from xfce-look.org.
in a long superuser-session i extracted them all into usr/share/themes, but some just failed to show up in settings->appearance or settings->window manager.
really irritating, because i just could not see *why*.
solution: permissions were not given for some folders. they should all have at least read-only access for all users.
maybe this helps.
:popcorn:

---

