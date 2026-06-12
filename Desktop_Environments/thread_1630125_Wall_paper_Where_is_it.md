---
title: "Wall paper Where is it"
date: 2010-11-24
forum: Desktop Environments
---

### Post by dontgetshocked on 2010-11-24
Hi,I am trying to find out where the wallpaper files are located because I want to copy some files to that folder.I looked in user/share/backgrounds but this is not where they are.I see some rotating backgrounds on my desktop but for the life of me cant find where they are.
Thanks,
PS Using PinguyOS 10.10

---

### Post by howefield on 2010-11-24
> **dontgetshocked said:**
> I looked in user/share/backgrounds but this is not where they are.

Presumably you tried usr/share/backgrounds/ ?

---

### Post by dontgetshocked on 2010-11-24
Yes I did look there but could not find the images that are used for my ever changing backgrounds.

---

### Post by stinkeye on 2010-11-24
Have a look at ~/.gnome2/backgrounds.xml
I think this should tell you where the wallpapers are that you've added.

---

### Post by dontgetshocked on 2010-11-24
Are you saying that the backgrounds are contained in one file?

---

### Post by stinkeye on 2010-11-24
I'm not sure how it works, but if I add a picture to Appearances it shows up in this file showing it's original location.
So it appears to get all the images from /usr/share/backgrounds plus the location of pictures you've added.

```
<wallpapers>
&#8722;
<wallpaper deleted="false">
<name>blacksurf.jpg</name>
<filename>[COLOR="Magenta"]/home/glen/Pictures/wallpaper/blacksurf.jpg[/COLOR]</filename>
<options>zoom</options>
<shade_type>solid</shade_type>
<pcolor>#2c2c00001e1e</pcolor>
<scolor>#2c2c00001e1e</scolor>
</wallpaper>
&#8722;
<wallpaper deleted="false">
<name>Feather</name>
<filename>/usr/share/backgrounds/Feather_by_quinn.anya.jpg</filename>
<options>zoom</options>
<shade_type>solid</shade_type>
<pcolor>#000000000000</pcolor>
<scolor>#000000000000</scolor>
```

---

### Post by wojox on 2010-11-24
They are in /usr/share/backgrounds

```
cd /usr/share/backgrounds
```

```
ls
```

---

### Post by stinkeye on 2010-11-24
If you open Appearances and hover over the wallpaper it shows the location.

---

### Post by dontgetshocked on 2010-11-24
Thanks, got this by the tail.

---

