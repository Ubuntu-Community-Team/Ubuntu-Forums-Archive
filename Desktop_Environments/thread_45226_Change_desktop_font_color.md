---
title: "Change desktop font color"
date: 2005-06-29
forum: Desktop Environments
---

### Post by PvNugteren on 2005-06-29
Hello everybody!

I've been searching for quite a while, but I still can't find a way to change the font color of the text underneath the icons on my desktop. Does anybody have an idea?

P.

---

### Post by SFN on 2005-06-29
As far as being able to do exactly what you requested, you'd need to edit the gtkrc file for the them you are currently using. However, none of the themes that come with Ubuntu have specific fonts setup. That means the existing gtkrc won't have a line you can change. How you would add lines that specify fonts is beyond the scope of my knowledge, so you might google for a nice gtkrc HOWTO.

For a more basic way to change font colors, you can use COG (GNOME Configurator). This will allow you to change font colors for Normal, Active, Prelight, Selected and Insensitive. That may change fonts other than Desktop - I'm not really sure.

To get it, do

```
wget http://www.krakoa.dk/progs/cog/cog-0.8.0-1.i386.rpm
```

Then, use alien to make deb packages:

```
sudo alien --to-deb cog-0.8.0-1.i386.rpm
``` 

and install the deb package:

```
sudo dpkg -i cog_0.8.0-2_i386.deb
``` 

Finally, refresh the menu:

```
sudo killall gnome-panel
``` 

Go to Application, System Tools, GNOME Configurator. Choose the Theme Panel, click the checkbox for "Enable setting theme colors" and chnage the colors for the various font states.

Hope this helps.

---

### Post by PvNugteren on 2005-06-30
SFN,

thanks! That was a very informative reply, you actually taught me more than one thing! I'll try it out, if it works, I'll let you know. I will also look for a gtkrc-HOWTO. If I find the solution, I'll post it here...

Thanks again,

Pascal

---

### Post by denisesballs on 2005-11-08
I don't see anywhere to change the desktop font color in this program?

---

### Post by TerpInHotLanta on 2008-02-07
The desktop font color is controlled by the theme.

System>Preferences>Appearence

Click on Customize in the theme section

and adjust the Window Text color

Why window text color and desktop text color are tied together, beats me.

---

### Post by TerpInHotLanta on 2008-02-07
To clarify, the window text color controls the color of text in the panels.

Additionally, some themes (read: Human) do not allow the adjusting of colors-- why? I have no idea, but it is really annoying.

---

