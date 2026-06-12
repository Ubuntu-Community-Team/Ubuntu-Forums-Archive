---
title: "glslideshow Screensaver not switching pictures"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Laenny on 2007-10-23
Hello dear fellow Ubuntu Users!

I managed to set up glslideshow in Ubuntu 7.10 to use my personal imageDirectory by creating an appropiate .xscreensaverrc with xscreensaver-demo.

BUT: Currently I have the issue that glslideshow only randomly picks a single picture from that directory and slides "between" that single image, resulting in a very boring slide show.

Any ideas, what might be causing this?

I had been using OpenSUSE 10.2 before, and there glslideshow randomly chose pictures and slided between all of them ...

Thanks in advance,
Carsten

---

### Post by bhp0528 on 2007-10-24
I presume you have an answer already but if not this [[COLOR="RoyalBlue"]ubuntuforum[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-212512.html") appears to be on the money.

---Correction---

that forum isn't applicable to 7.10 so you need to check out [this guy]("http://www.computechgroup.com/?p=328"). His information is more appropriate for the current version. To be specific you need to use terminal and then run:
```
sudo gedit /usr/share/applications/screensavers/glslideshow.desktop
```
You then need to find the line that says
```
Exec=glslideshow -root
```

Change the text to show::
```
Exec=glslideshow -root -duration 15 -pan 15 -fade 5
```


If you need to known why then run **man glslideshow**:
>        -duration **seconds**
               How long each image will be displayed before loading a new one.
               Default 30 seconds.

       -pan **seconds**
               How long each pan-and-zoom should last.  Default 6 seconds.

               With the default settings of -pan 6 -duration  30,  each  image
               will  be displayed five times (30/6), and then a new image will
               be loaded. [U] If you want a new image to be loaded at each  fade,
               then set -pan and -duration to the same value.[/U]

       -fade **seconds**
               How long each cross-fade between images should last.  Default 2
               seconds.  If set to 0, then no cross-fading will be  done  (all
               transitions will be jump-cuts.)
Why these are the defaults is beyond me ... it's burned too many hours of my life ... both for Ubuntu 7.04 and 7.10.

---

### Post by Laenny on 2007-10-24
Hi,

thanks for your answer, but it does NOT solve my problem.

The symptom can be further described like that:

GLslideshow SEEMS to switch pictures, quite often, but always loads the same picture...

Regards,
Carsten

---

### Post by bhp0528 on 2007-10-25
> I managed to set up glslideshow in Ubuntu 7.10 to use my personal imageDirectory by creating an appropiate .xscreensaverrc with xscreensaver-demo.

Ah... yes I suppose if I had read your question then perhaps my help would have been relevant. Using xscreensaver-demo makes a difference, see below. 

> GLslideshow SEEMS to switch pictures, quite often, but always loads the same picture...

This is usually the default glslideshow setting. After I installed the xscreensaver and ran the xscreensaver-demo I appeared to have the same issue. I did notice  the image changes after a long while. If you wait long enough (8 - 10 minutes) do you get another picture? If it does then you should just have to reconfigure your settings. With xscreensaver you have two options:

**1: GUI** - Open xscreensaver-demo > glslideshow > settings and then set the **"Time until loading new image"** down to *10 seconds*. If tweaking this doesn't help then you might need to go in manually again. :(

**2: Gedit** - Although the code I gave you before was accurate the xscreensaver settings are in a different spot than ubuntu's default location. So instead of going to /usr/share/applications/screensavers/glslideshow.desktop you need to edit:

```
~/.xscreensaver
```

.xscreensaver will have configs for all screensavers, not just glslideshow so you need to find the line that starts with **glslideshow** and then add the code from before. If that works ... good for you. If not  ... use one totally awesome picture so it isn't lame when panning over and over. OK not really but I might have less to say next time. Best of luck.

---

### Post by LaVache on 2007-11-06
Good writeup here on how to manage the settings for glslideshow:

[http://rclermont.blogspot.com/2007/02/modifying-glslideshow-settings-in_28.html]("http://rclermont.blogspot.com/2007/02/modifying-glslideshow-settings-in_28.html")

This fixed the "same image being loaded over and over" problem for me.

---

### Post by dillthedog on 2008-07-07
> **Laenny said:**
> Hi,

thanks for your answer, but it does NOT solve my problem.

The symptom can be further described like that:

GLslideshow SEEMS to switch pictures, quite often, but always loads the same picture...

Regards,
Carsten

Hmmm, it may not be relevant, but I've had a similar problem. My setup is:

xscreensaver 5.04
Ubuntu 8.04 (hardy)
Gnome 2.22.2

What I do is have a directory /jlinks that I use to selectively point, using soft links, to various images in my main photo filesystem, /jpegs. (I have a couple of scripts that I use to grep and find certain files according to patterns in their names.)

What I found was that if I changed the contents of the /jlinks directory, by either adding or removing links, the change was not picked up by GLSlideshow. Killing the daemon or restarting the Xserver had no effect. 

I found two ways to get GLSlideshow to 'rescan' the target folder.

1. Run xserver-demo and under the Advanced tab change the 'Choose Random Image' from entry to something else. e.g. /tmp. Then change it back again.

2. Remove the file .xscreensaver-getimage.cache (this is in my home directory). 

If you have a short interval for the image change xscreensaver-demo seems to print some debug info that shows it trying to find files from .xscreensaver-getimage.cache and not finding them.

This may be entirely unrelated to your setup but the symptoms seem similar.

Dougie

---

