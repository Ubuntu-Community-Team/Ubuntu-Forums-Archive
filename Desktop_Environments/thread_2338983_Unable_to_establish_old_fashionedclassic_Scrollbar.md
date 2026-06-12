---
title: "Unable to establish old fashioned/classic Scrollbars"
date: 2016-10-03
forum: Desktop Environments
---

### Post by Buggy_Bison on 2016-10-03
Dear experts

I know this question has been asked before, but none of the usual solutions is working for me.

I have installed Ubuntu 16.04 on a Thinkpad Carbon X1. I have also installed gnome-panel, gnome-flashback and gnome-session-flashback, and I am currently using the Gnome (Metacity) desktop rather than unity.

I am trying to replace the thin overlay scrollbars that appear along the right edges of windows, with the old classic scrollbars that look like a solid bar with rounded ends. This is a matter of accessibility because some of us can't see well enough to cope with the overlay scroll bars.

I have tried the following and, for example, on my terminal, I am still getting a thin orange strip that appears when I mouse over it, rather than a nice chunky scroll bar:

export GTK_OVERLAY_SCROLLING=0 # also this is added to /etc/environment

dconf-editor and un-ticking “ubuntu-overlay-scrollbars” from [I]org -> gnome -> desktop -> interface

unsettings [/I]and turning overlay scrollbars off

I tried unity-tweak-tool but it would not let me choose legacy in the scrolling tab (grayed out)

sudo apt-get remove overlay*I added gtk-primary-button-warps-slider = false to /etc/gtk-3.0/settings.ini

None of these has modified the appearance of my scrollbars from that of the original install.

Clearly, this is not as simple as described in the "**How to restore the classic scroll bar"** titled web pages.

Thank you very much for any advice on what I am doing wrong and on how to restore those old 1990's scroll bars!

Buggy

---

### Post by TheFu on 2016-10-03
Don't know how to do what you want, but perhaps running fvwm would work?  Then everything controlled by the WM is in your control. Width, color; all under your control with a normal .rc file.

Is 1995 "old-school?"

---

### Post by vasa1 on 2016-10-03
> **Buggy_Bison said:**
> ..
export GTK_OVERLAY_SCROLLING=0 # also this is added to /etc/environment

dconf-editor and un-ticking “ubuntu-overlay-scrollbars” from [I]org -> gnome -> desktop -> interface

unsettings [/I]and turning overlay scrollbars off

I tried unity-tweak-tool but it would not let me choose legacy in the scrolling tab (grayed out)

sudo apt-get remove overlay*I added gtk-primary-button-warps-slider = false to /etc/gtk-3.0/settings.ini

None of these has modified the appearance of my scrollbars from that of the original install.

Clearly, this is not as simple as described in the "**How to restore the classic scroll bar"** titled web pages.

Thank you very much for any advice on what I am doing wrong and on how to restore those old 1990's scroll bars!

Buggy
Re. *I added gtk-primary-button-warps-slider = false to /etc/gtk-3.0/settings.ini*, also add it to *~/.config/gtk-3.0/settings.ini*. FWIW, I don't use spaces on either side of "=" in "gtk-primary-button-warps-slider = false".

---

### Post by CantankRus on 2016-10-04
This thin line scrollbar which expands when hovered seems to be set in the theme and I can't find an
easy way to disable it other than use a different theme or edit the theme.

eg: to edit the default Ambiance theme...
I'm going to use "gksudo gedit" here which requires the installation of **gksu**.
Alternatively you can use "sudoedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css" which will use the default editor(nano)
```
gksudo gedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css
```

Hit ctrl+f and type in "scrollbar" followed by a space.
Should take you to the section as in pic.
[ATTACH=CONFIG]271487[/ATTACH]

Scroll down to line  1236 and change the three instances of 7px to 0px
as[COLOR="#FF0000"] highlighted[/COLOR] below.
(Note: you can also set the scrollbar width with [COLOR="#EE82EE"]GtkRange-slider-width[/COLOR])
```
/*************
 * scrollbar *
 *************/
.scrollbar {
    -GtkScrollbar-has-backward-stepper: 0;
    -GtkScrollbar-has-forward-stepper: 0;
    -GtkScrollbar-trough-border: 0;
    -GtkScrollbar-min-slider-length: 31;
    -[COLOR="#EE82EE"]GtkRange-slider-width[/COLOR]: 12;

    background-color: @scrollbar_track_color;
    background-image: none;
    background-size: 0;
    border: none;
    border-radius: 0;
}

.scrollbar.overlay-indicator {
    background-color: transparent;
}

.scrollbar:hover,
.scrollbar.dragging {
    background-color: @scrollbar_track_color;
}

.scrollbar:hover:backdrop,
.scrollbar.dragging:backdrop {
    background-color: @backdrop_selected_bg_color;
}

/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to keep the slider smaller, but keeping few threshold pixels
 */
.scrollbar.vertical:hover:dir(ltr),
.scrollbar.vertical.dragging:dir(ltr) {
    margin-left: 2px;
}

.scrollbar.vertical:hover:dir(rtl),
.scrollbar.vertical.dragging:dir(rtl) {
    margin-right: 2px;
}

.scrollbar.horizontal:hover,
.scrollbar.horizontal.dragging,
.scrollbar.horizontal.slider:hover,
.scrollbar.horizontal.slider.dragging {
    margin-top: 2px;
}

.scrollbar.slider {
    background-color: alpha(@selected_bg_color, 0.8);
    border-radius: 3px;
}

.scrollbar.slider.hovering,
.scrollbar.slider.dragging {
    border-radius: 2px;
    margin: 0;
}

/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to define some kind of proximity effect also on mouse-enter
 */
.scrollbar.slider.vertical:dir(ltr):not(:hover):not(.dragging) {
    margin-left: [COLOR="#FF0000"]7px[/COLOR];
}

.scrollbar.slider.vertical:dir(rtl):not(:hover):not(.dragging) {
    margin-right: [COLOR="#FF0000"]7px[/COLOR];
}

.scrollbar.slider.horizontal:not(:hover):not(.dragging) {
    margin-top: [COLOR="#FF0000"]7px[/COLOR];
}
```
Save and close.
[ATTACH=CONFIG]271488[/ATTACH]
May have to log out and back in or use a tweak tool to change themes then back to Ambiance.

---

### Post by TheFu on 2016-10-04
setenv EDITOR={whatever you like}
Then use sudoedit. Much safer.

EDITOR has been around since the beginning.

---

### Post by CantankRus on 2016-10-04
> **TheFu said:**
> setenv EDITOR={whatever you like}
Then use sudoedit. Much safer.

EDITOR has been around since the beginning.
Thanks, that's better than using gksu in forums....
```
EDITOR=gedit sudoedit [COLOR="#808080"]/path/to/file[/COLOR]
```

---

### Post by Buggy_Bison on 2016-10-04
CantankRus's suggestion of editing a theme has worked - I now have permanent scrollbars of any thickness I might want.

I have migrated to Ubuntu from Linux Mint, which tended to make these tweaks simpler.

Thank you very much CantankRus.

@TheFu 1995 is "old school" - when I have more time, I may try getting back total control over the WM

---

### Post by TheFu on 2016-10-04
If you put **export EDITOR=gedit** into your ~/.bashrc file, then you don't need to deal with it again ... provided that program exists on the system AND there is a working X/Server.  Personally, I think that is a mistake (never assume everyone runs a desktop distro), but if you run a desktop with gedit, it will be fine. If gedit isn't installed (and it isn't always), then someone new will just be confused and isn't that the point here - to avoid confusion for new people while being technically correct?  That is why nano is the default today - works on desktops and servers.

Any program that uses/needs an editor should honor the EDITOR environment variable. It has been around and used at least 35 years - perhaps 45 years.

---

### Post by vasa1 on 2016-11-21
jerboa2 has a thread here: [https://ubuntuforums.org/showthread.php?t=2343900](https://ubuntuforums.org/showthread.php?t=2343900)

jerboa2's post and its responses have now been merged into that thread.

---

