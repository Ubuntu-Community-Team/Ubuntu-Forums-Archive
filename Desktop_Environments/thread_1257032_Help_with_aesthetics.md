---
title: "Help with aesthetics"
date: 2009-09-03
forum: Desktop Environments
---

### Post by Bananaloaves on 2009-09-03
I am sorry that I do not have a screen-shot. I am running a non Linux OS at the moment.

Ok, so here is my problem, and I will try to explain it to the best of my ability.

I have my ubuntu installation looking very much like OS X. The only problem I have is the top panel.  I set an image to the top panel, to give it the translucent appearance used in Leopard (I know I can make the panel translucent itself, but I need more of a gradient). All is good with that, except that in that panel, where it says applications, places, and system, the panel does not bear the picture and is solid Grey. It really disrupts how the top panel looks. If a screen-shot is absolutely needed than I can make one. Is there any way to fix that so that my panel flows all the way across.

Also, how do I change the gnome logo to a custom picture in the very top left of the top panel?

I am running Jaunty w/ gnome.

---

### Post by coldReactive on 2009-09-03
Might want to try mac4lin if you haven't:

[http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)

---

### Post by Bananaloaves on 2009-09-03
I got the themes from mac4lin. I guess the site I went to had them separate. I installed AWN myself. If I was to download it again and reapply it, is there anything that can go wrong?

---

### Post by coldReactive on 2009-09-03
I wouldn't know, I don't use mac4lin because default metacity is enough for me usually.

---

### Post by mcduck on 2009-09-03
> **Bananaloaves said:**
> I am sorry that I do not have a screen-shot. I am running a non Linux OS at the moment.

Ok, so here is my problem, and I will try to explain it to the best of my ability.

I have my ubuntu installation looking very much like OS X. The only problem I have is the top panel.  I set an image to the top panel, to give it the translucent appearance used in Leopard (I know I can make the panel translucent itself, but I need more of a gradient). All is good with that, except that in that panel, where it says applications, places, and system, the panel does not bear the picture and is solid Grey. It really disrupts how the top panel looks. If a screen-shot is absolutely needed than I can make one. Is there any way to fix that so that my panel flows all the way across.

Also, how do I change the gnome logo to a custom picture in the very top left of the top panel?

I am running Jaunty w/ gnome.

The problem is that the GTK2 theme you are using is defining background for panel applets, and this will override any themeing you do directly from the panel's options.

You'll have to edit the GTK2 theme and remove the backgrounds from the panel applets. Quite many themes have a separate panel-rc or similar file that includes all panel-related themeing, in that case simply removing or renaming that file does the trick. If there isn't such a file, you'll just have to go through the main theme rc file, search for all panel-specific stuff and remove it.

After removing the panel themeing from the GTK2 theme your panel background will work correctly and apply to the whole panel and all applets inside it.

(This is one of the reasons I really dislike the recently popular idea of adding panel background trough the GTK2 theme. The other is that backgrounds applied through GTK2 theme won't scale or rotate correctly to fit different panel sizes or vertical panels, while backgrounds applied directly from the panel's options will if you just enable the options in gconf..)

---

