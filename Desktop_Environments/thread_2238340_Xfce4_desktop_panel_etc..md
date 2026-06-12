---
title: "Xfce4 desktop panel etc."
date: 2014-08-07
forum: Desktop Environments
---

### Post by gordon99 on 2014-08-07
There are a couple of aspects which I wish to change on the xfce4 desktop if this is possible. The first one relates to the top panel. I have some difficulty reading the time and date numbers and wonder if they can be increased in size. I increased the height of the panel thinking this would increase the size of the symbols and time/date letters and numbers but i don't think it has. Secondly, the digital time clock shows up twice on the panel and I wonder if one can be removed.

There is another matter in a similar vein which I wish I could alter. The symbols one clicks to hide, enlarge or delete web pages are very small and therefore indistinct. Can these be enlarged please and if they can, how?

---

### Post by Dennis N on 2014-08-07
The font of the clock and window buttons on the panel is set by the default font. Change the default font and size and you also change the panel font and size.

**Settings > Appearance > Fonts Tab**

Two Clocks?

**Right Click on Panel > Panel > Panel Preferences > Items**

Check for two clock entries and remove one by selecting it and clicking the red X.

> The symbols one clicks to hide, enlarge or delete web pages...

Where are they? In the web browser?

---

### Post by vasa1 on 2014-08-07
> **gordon99 said:**
> ...
There is another matter in a similar vein which I wish I could alter. The symbols one clicks to hide, enlarge or delete web pages are very small and therefore indistinct. Can these be enlarged please and if they can, how?
Could OP be meaning the min/max/close buttons of the window manager?

---

### Post by ajgreeny on 2014-08-07
> **vasa1 said:**
> Could OP be meaning the min/max/close buttons of the window manager?
Good call; you could be right!

In which case go to **Settings-manager ->Window-manager ->Style** tab and play around there to get the window control buttons that you prefer.  You can change a lot of other details in that dialogue as well as just the buttons.

---

### Post by Dennis N on 2014-08-07
I have given up some time ago guessing what a poster means. In this one, I could guess that enlarge means zoom - hence a reference to Firefox's zoom buttons. And delete? There is no delete page button or icon in Firefox's UI. He or she could and should clarify the matter with a follow up post.

---

### Post by gordon99 on 2014-08-08
Thanks everybody for pointing me in the right direction. I have managed to make some of the desktop adjustments I was hoping to make. You are on the ball vasa 1 when you suggested I was referring to the min-min-max-close buttons. I've not yet found how to enlarge these. Maybe one can't. Not knowing the correct terminology is sometimes the biggest difficulty in asking for help.

---

### Post by vasa1 on 2014-08-08
> **gordon99 said:**
> ... I was referring to the min-min-max-close buttons. I've not yet found how to enlarge these. Maybe one can't. Not knowing the correct terminology is sometimes the biggest difficulty in asking for help.
I don't use Xubuntu or XFCE now but I seem to remember being told that the only way to have larger min/max/close buttons is to use a larger font in the title bar. (That is true of my current window manager, Openbox.)

But, as ajgreeny suggested, do look at Settings-manager -> Window-manager -> Style for options.

---

### Post by Dennis N on 2014-08-08
I also think you would have to use a different window manager theme with larger or different style buttons that are easier to see. Vasa1's comment about openbox and changing the font size unfortunately didn't make the window title bar wider (or buttons larger) in xfce4 window manager (looked a four themes only) - the width is fixed and it just cuts off the text.

None of the themes that come with Xubuntu looks very promising. You might try Ambiance - at least it has an orange close button that is easy to see.

[http://gnome-look.org/content/show.php/Ambiance+light+fixed?content=164118](http://gnome-look.org/content/show.php/Ambiance+light+fixed?content=164118)

---

### Post by ajgreeny on 2014-08-08
No the font size change suggested does nothing, but there are certainly many themes on my machine which have large and/or coloured min/max/close buttons making them easier to use, eg.
Coloured buttons:-
Agua
Agualemon
Gnububble
Pills

Large buttons:-
Alternate
Atlanta
Defcon-IV
Gtk
Microdeck
Piranha
Prune
RedmondXP (also coloured)

And many more.

Make sure you have the **xfwm4-themes** package installed and you should find most if not all of them.

---

### Post by pretty_whistle on 2014-08-08
I have Xfce and here's how I did it:

As far as increasing the font size for the date and time, there's only one way I know of.  Install "Xfce goodies" from the software center.  It's a package of programs you can add to the panel, one of which is date and time.  Choosing date and time from this list includes a setting for font size.  Just right click it and choose "properties".

---

### Post by Dennis N on 2014-08-08
> As far as increasing the font size for the date and time, there's only one way I know of.

Just to clarify the Xubuntu clock plugins:

There are at least two possible clock plugins. The default clock panel plugin in Xubuntu 14.04 is called "clock". It has no independent settings for font size, but automatically sets it's font to the default font. Back with Xubuntu 12.04, the default clock panel plugin was "Date Time" - probably the one you are referring to. That one had the independent font setting you describe. Clock has some layouts that were not there in 'Date Time', such as LCD display, analog, binary and fuzzy.

If you use XFCE desktop environment instead of Xubuntu 14.04, there could be a difference in the default plugin provided.

---

### Post by ajgreeny on 2014-08-08
In 12.04 using the datetime applet which I think has gone from 14.04 it was possible to choose the font and its size in the right click ->Properties dialogue box.

No, it has not gone; I have just looked in my VM of 14.04 and the datetime plugin is still available but not installed by default, so just install it, then right click ->Properties and play with the settings.

I have **droid-sans bold** font and custom settings of **%a, %d %b - %R**

---

