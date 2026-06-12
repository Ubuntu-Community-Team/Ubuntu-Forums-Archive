---
title: "How to get rid of these scroll bars"
date: 2017-08-29
forum: Desktop Environments
---

### Post by James Wilde on 2017-08-29
The last few versions (I'm using 16.04) of Ubuntu have had a new style of scroll bar.  It's not there when you need it and it's often a devil of a job to get it to show up and stay showing up long enough to grab it and draw.  And the useful little arrows at top and bottom are gone.

Is there any way to get them all back?  Proper scroll bars which stay there all the time, and the little arrows?  Do I have to backtrack to, say, 12.04 or even earlier?  Are they there if I migrate to kubuntu, lubuntu, edubuntu or another?  Will I find them if I go over to Mint or another offshoot from Ubuntu?  Or, worst case, are they there in Debian, Fedora, Black Hat, Suse?

Heeeeelp!

---

### Post by again? on 2017-08-29
This will stop them hiding.
```
echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment
```
Log out.
They are a PITA.

---

### Post by James Wilde on 2017-08-29
Good try Guber2, but no cigar.  I checked and I had already inserted that into my /etc/environment file last time I tried to solve this problem.

BTW does it make any difference that I am using the classic Gnome fallback?  Does your solution only work with Unity?

---

### Post by vasa1 on 2017-08-29
I've edited the title of this thread and another post in this thread. 

From the [Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules"):> Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.

---

### Post by again? on 2017-08-29
It works to make the scrollbar margin always visible but the default Ambiance theme also has a setting that decreases the thickness of the scrollbar until mouse hover.
Solution: Change themes.
_arc-dark_
[ATTACH=CONFIG]276537[/ATTACH]

_Ambiance_
[ATTACH=CONFIG]276538[/ATTACH]

---

### Post by vasa1 on 2017-08-29
And this may also help:```
[Settings]
gtk-font-name=Hack 12
gtk-theme-name=g3bird
gtk-icon-theme-name=breeze
gtk-fallback-icon-theme=oxygen
gtk-cursor-theme-name=oxy-violet
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=1
gtk-button-images=0
gtk-primary-button-warps-slider=0

```It's the first and last lines that are important to get back "legacy scrolling": [https://wiki.archlinux.org/index.php/GTK%2B#Legacy_scrolling_behavior](https://wiki.archlinux.org/index.php/GTK%2B#Legacy_scrolling_behavior).

The file should be called *settings.ini* and be placed in *~/.config/gtk-3.0*.

---

### Post by James Wilde on 2017-08-29
High Contrast did it - at least the scroll bars.  I suppose I will have to live without the arrows.  Actually I don't have Ark-Dark.  I only have three, Ambience, Raddiance and High Contrast.  But now I notice that the icon names are black on purple!  I'll see what Vasa1's suggestion has for success.  Maybe there is somewhere I can change the icon titles to white - or the background to something other than purple.

Thanks, Guber2.

---

### Post by vasa1 on 2017-08-29
My suggestion only addresses the consequence of what happens when you click in the trough of the scrollbar. It won't help the appearance.

For the up and down arrows, if your theme supports them, the advice in [https://ubuntuforums.org/showthread.php?t=2152526&p=12683902#post12683902](https://ubuntuforums.org/showthread.php?t=2152526&p=12683902#post12683902) should work.

An easier way maybe this: [https://ubuntuforums.org/showthread.php?t=2354329&p=13614620#post13614620](https://ubuntuforums.org/showthread.php?t=2354329&p=13614620#post13614620)

---

### Post by p0p2 on 2017-08-29
Have you guys tried Gnome Color Chooser ?
There is an option to apply the scrollbar you want belonging to another theme (gtk engine).
Since you want arrows,i recommend you to use the scrollbar of the theme "Thinice" .

---

### Post by again? on 2017-08-29
> **p0p2 said:**
> Have you guys tried Gnome Color Chooser ?
There is an option to apply the scrollbar you want belonging to another theme (gtk engine).
Since you want arrows,i recommend you to use the scrollbar of the theme "Thinice" .

gnome-color-chooser is an old application that works with gtk+2 applications.

---

### Post by again? on 2017-08-31
> **James Wilde said:**
> High Contrast did it - at least the scroll bars.  I suppose I will have to live without the arrows.  Actually I don't have Ark-Dark.  I only have three, Ambience, Raddiance and High Contrast.  But now I notice that the icon names are black on purple!  I'll see what Vasa1's suggestion has for success.  Maybe there is somewhere I can change the icon titles to white - or the background to something other than purple.

Thanks, Guber2.

If you want keep using the default Ambiance theme on 16.04 you can create a custom config to override the theme.
```
gedit ~/.config/gtk-3.0/gtk.css
```

Copy and paste this into it and save.
```
/*************
 * scrollbar *
 *************/
.scrollbar {    
    -GtkRange-slider-width: 12;
}



/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to define some kind of proximity effect also on mouse-enter
 */
.scrollbar.slider.vertical:dir(ltr):not(:hover):not(.dragging) {
    margin-left: 0px;
}

.scrollbar.slider.vertical:dir(rtl):not(:hover):not(.dragging) {
    margin-right: 0px;
}

.scrollbar.slider.horizontal:not(:hover):not(.dragging) {
    margin-top: 0px;
}



/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to keep the slider smaller, but keeping few threshold pixels
 */
.scrollbar.vertical:hover:dir(ltr),
.scrollbar.vertical.dragging:dir(ltr) {
    margin-left: 0px;
}

.scrollbar.vertical:hover:dir(rtl),
.scrollbar.vertical.dragging:dir(rtl) {
    margin-right: 0px;
}

.scrollbar.horizontal:hover,
.scrollbar.horizontal.dragging,
.scrollbar.horizontal.slider:hover,
.scrollbar.horizontal.slider.dragging {
    margin-top: 0px;
}


/* slider color and radius */
.scrollbar.slider {
    background-color: alpha(@selected_bg_color, 0.6);
    border-radius: 5px;
}

.scrollbar.slider.hovering,
.scrollbar.slider.dragging {
    background-color: alpha(@selected_bg_color, 0.8);
    border-radius: 5px;
}
```

You can alter the width of the scrollbar with the first setting "-GtkRange-slider-width: **12**;"
Logout after making changes.

Pic using **20** width just to illustrate.

---

### Post by James Wilde on 2017-09-18
Interesting, p0p2.  Thanks for the tip.

---

