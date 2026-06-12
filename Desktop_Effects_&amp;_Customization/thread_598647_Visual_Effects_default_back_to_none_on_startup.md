---
title: "Visual Effects default back to none on startup"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by Kevan on 2007-10-31
I love compiz-fusion effects on Gutsy. I'm using  the restricted Nvidia drivers and they seem to work fine. The problem I have is that every time I restart, the appearance > visual effects default back to none.

I have tried clearing compiz and reinstalling it, getting rid of all previous versions (I think), but this didn't make any difference. 

Does anyone know how I can get my visual effects to default properly to Normal/Extra or Custom?

---

### Post by Forlong on 2007-10-31
What's the output of
```
cat ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```
and
```
ls ~/.config/autostart
```

---

### Post by Kevan on 2007-11-01
Thanks for your reply. Did as requested. Here's the output:

```
?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1193942008" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
        <entry name="default" mtime="1193851558" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
```

and 

```
compiz.desktop]
```

Does this help?

---

### Post by Forlong on 2007-11-01
Yes, you have to remove that:
```
rm ~/.config/autostart/compiz.desktop
```

Or via **System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs**

---

### Post by Kevan on 2007-11-01
Brilliant! Thanks that's got it working.

Gnome has got quite slow on startup though. Once in everything is very speedy. Is there anything I can do to speed up gnome loading?

---

