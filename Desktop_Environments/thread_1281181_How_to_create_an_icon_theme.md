---
title: "How to create an icon theme?"
date: 2009-10-03
forum: Desktop Environments
---

### Post by Ordes on 2009-10-03
Hello, i was an old skinner in windows, but i am a new skinner in ubuntu...

i am trying to create an icon set. i was looking through the standard human set to get an idea. but now i have even more questions.

i was googeling a lot, but couldnt find the needed information. Hope someone her can help me out:


1. The icons are all in different sized folders (8-48 ) and one scaleable (32-256). When i have scalable icons, why i need the other folders? couldnt i just make scalable only (8-256)?

2. If i need to have all those folders. Is there an application to bulk convert? e.g i finished my scalable folder, or 48 folder. To run an app that converts those folder in other sizes? otherwise its a lot of work, for not much output.

thanks

---

### Post by anonymous_user on 2009-10-03
The SVG is typically used for only large sizes. If you use it for small sizes it will not look as good as an icon made specifically for that small size.

16px:

[img]http://www.zwixy.com/images/482368528documentopen.png[/img]

16px (scaled from SVG):

[img]http://www.zwixy.com/images/1306826363folderscale.png[/img]

---

### Post by barthel on 2009-10-03
The documentation for the Tango project explains the rationale fairly well. Look at "Sizes" on [http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines]("http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines")

Basically, it's because scaling only works to a point. Dependng upon the complexity of the large image, you can only scale down so far before you can no longer recognize what the icon is supposed to represent.

You can try exporting your SVGs to 22x22 and 16x16 PNGs, but the 16x16s will probably have to be done from scratch.

Yes, it is a LOT of work. That's why there are so few good icon sets out there.

---

### Post by Ordes on 2009-10-03
thanks so far.. you basicly conformed what i was afraid of... 

----
any ideas if there is a batch converter for the pngs. would make work a little bit easier...

----
mhm... skinning icon themes, might be one of the few things where windows is more comfortable than ubuntu... :(  

did a lot of themes before on windows machines... looking at this amount of time consuming work for one gnome theme, is a little bit depressing...

---

