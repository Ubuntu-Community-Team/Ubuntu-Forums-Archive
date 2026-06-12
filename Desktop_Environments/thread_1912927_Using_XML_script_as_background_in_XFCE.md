---
title: "Using XML script as background in XFCE"
date: 2012-01-21
forum: Desktop Environments
---

### Post by OstensiblyFeet on 2012-01-21
I've recently switched to XFCE from Gnome. All in all, I'm very happy with it. The functionality is pretty much exactly what I was looking for, bar a couple of things.

One thing I had under Gnome 2 was a lovely desktop background with transitioning images for the time of day. It ran as an xml script, but XFCE is having none of it unfortunately.

Now I'm not sure if this is down to XFCE refusing xml scripts as an input for the wallpaper, or if it's because the script was written for Gnome and XFCE doesn't like it.

I'm not asking anyone to rewrite it for me, unless it's particularly easy to do, but if anyone could point me to some resources which would allow me to write it in a way XFCE would understand, either as an XML or a bash script that would be cool.

I've found resources for doing something similar to this via bash scripts and the crontab, but what I'm keen to do is retain the transitioning overlay so the changes aren't jerky.

The Wallpaper incidentally is called AllDayLong, and the fully functioning version for Gnome can be found here:

[http://gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443](http://gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443)

Here is the script:

<background>
<starttime>
<year>2012</year>
<month>01</month>
<day>21</day>
<hour>0</hour>
<minute>0</minute>
<second>01</second>
</starttime>

<static>
<duration>18000.0</duration>
<file>/media/Storage/Pictures/AllDayLong-Wallpaper/08.jpg</file>
</static>
<!-- il est 5h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/08.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/01.jpg</to>
</transition>
<!-- il est 7h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/01.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/02.jpg</to>
</transition>
<!-- il est 9h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/02.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/03.jpg</to>
</transition>
<!-- il est 11h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/03.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/04.jpg</to>
</transition>
<!-- il est 13h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/04.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/05.jpg</to>
</transition>
<!-- il est 15h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/05.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/06.jpg</to>
</transition>
<!-- il est 17h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/06.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/07.jpg</to>
</transition>
<!-- il est 19h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>/media/Storage/Pictures/AllDayLong-Wallpaper/07.jpg</from>
<to>/media/Storage/Pictures/AllDayLong-Wallpaper/08.jpg</to>
</transition>
<!-- il est 21h -->
<static>
<duration>10800.0</duration>
<file>/media/Storage/Pictures/AllDayLong-Wallpaper/08.jpg</file>
</static>
<!-- il est 0h -->
</background>

---

### Post by OstensiblyFeet on 2012-01-26
Bump. Don't suppose anyone could help me with that one?

I did have another XFCE desktop related question I don't know if anyone might be able to help with. Is there a way to make the background of the text on desktop icons darker? The reason being is that at the moment the background for the text is transparent - there might be some slight shading there, I'm not sure - and I'm not able to read the text on the icons properly against some wallpapers because the text is camouflaged.

---

### Post by LewisTM on 2012-01-26
About your second question, you need to create file ~/.gtkrc-2.0
and add the following lines:
```
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 100}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```
To get a transparent background, alpha should be set at 0, etc.
Save the file then reload the desktop by issuing the command
```
pkill xfdesktop
```
Cheers!

---

### Post by OstensiblyFeet on 2012-01-26
Hey Lewis

I do appreciate the feedback, unfortunately that doesn't seem to do anything. I tried setting the numbers at 0, 100 and 200 and then running the pkill desktop command, the appearance seemed to e exactly the same each time.

---

### Post by LewisTM on 2012-01-26
> **OstensiblyFeet said:**
> Hey Lewis

I do appreciate the feedback, unfortunately that doesn't seem to do anything. I tried setting the numbers at 0, 100 and 200 and then running the pkill desktop command, the appearance seemed to e exactly the same each time.

My bad, it should be 255 for a totally opaque background.
And to make sure the changes are applied, log out and back in.

---

### Post by Toz on 2012-01-26
The xml file is just a configuration file, the real work is in the script/program. I went to download the script from your link and unfortunately, it was hosted on megaupload, and well, thats a no go right now. How big is the executable script/program? Can you post it here or is there another place that it can be downloaded?

---

