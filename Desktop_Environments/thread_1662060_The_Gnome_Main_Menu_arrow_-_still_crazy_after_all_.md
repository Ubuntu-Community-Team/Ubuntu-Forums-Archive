---
title: "The Gnome Main Menu arrow - still crazy after all these years"
date: 2011-01-07
forum: Desktop Environments
---

### Post by tpprynn on 2011-01-07
I've just read this thread:

[http://ubuntuforums.org/showthread.php?t=733808](http://ubuntuforums.org/showthread.php?t=733808)

and the information it seems is a bit out of date and a risk to use. I felt more comfortable with the .gtkrc-2.0 file suggested a few posts in, but it doesn't work, in that it turns the panel to the Raleigh-themed one which we always get when there's some kind of error in a gtkrc file, as those of us that have dabbled in theming will know.

It's comical that this minor but unnecessary eyesore goes back so far and hasn't been dealt with, but is there any new info about this, a new method, for 10.10? I don't want to be doing compiling or to risk messing things up, as has been caused by the directions in the other thread, because I've been experimenting with different distros for two years, just bought a new hard drive, and have settled now.

Maybe someone here knows why the .gtkrc-2.0 file hasn't worked for me?  I twigged that the panel (though not the rest of the theme, i.e. in program windows) had turned to Raleigh because of those ugly handles pertaining to the Window List panel applet and the one to the left of the notification area. I used the exact file in that other thread, I tried logging out and in and then rebooting, and I even tried pasting the file's contents into the gtkrc file of the theme I use.

If you need to know, I'm using the 'Lush' Metacity window border and the 'Redmond' engine.

Thanks.

Any Gnome staff reading - an arrow one millimetre wide, I beg you, stop ignoring our wails of deep, deep, deep, despair......

This is the .gtkrc-2.0 file's contents for anyone not quite inspired to inspect the other thread:

style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"

---

### Post by tpprynn on 2011-01-10
I had a poke around in another theme and with a bit of trial and error have got rid of both the menu arrow and the ugly handles I mention. This gtkrc-2.0 file suits my white on grey panel and panel background. I didn't know how much should be removed for someone using a default undecorated panel but you can see what I've added.

style "panel-handle" 
{
    engine "pixmap"
    {    
        image
        {
        function    = HANDLE
        }    
 
    image
        {
            function    = HANDLE
        }
    }
}

style "panel"
{
fg[NORMAL] = "#FFFFFF"
fg[PRELIGHT] = "#FFFFFF"
fg[ACTIVE] = "#FFFFFF"
fg[SELECTED] = "#FFFFFF"
fg[INSENSITIVE] = "#FFFFFF"

bg[NORMAL] = "#5e5e5e"
bg[PRELIGHT] = "#5e5e5e"
bg[ACTIVE] = "#5e5e5e"
bg[SELECTED] = "#5e5e5e"
bg[INSENSITIVE] = "#FFFFFF"

base[NORMAL] = "#FFFFFF"
base[PRELIGHT] = "#FFFFFF"
base[ACTIVE] = "#FFFFFF"
base[SELECTED] = "#FFFFFF"
base[INSENSITIVE] = "#FFFFFF"

text[NORMAL] = "#FFFFFF"
text[PRELIGHT] = "#FFFFFF"
text[ACTIVE] = "#FFFFFF"
text[SELECTED] = "#FFFFFF"
text[INSENSITIVE] = "#FFFFFF"
}

widget "*PanelWidget*"             style "panel"
widget "*PanelApplet*"             style "panel"
class "*Panel*"                 style "panel"
widget_class "*Mail*"             style "panel"
class "*notif*"                 style "panel"
class "*Notif*"                 style "panel"
class "*Tray*"                 style "panel"
class "*tray*"                 style "panel"
widget "*fast-user-switch*"        style "panel"
widget "*CPUFreq*Applet*"            style "panel"
widget "*indicator-applet*"        style "panel"
class "PanelApp*"            style "panel"
widget_class "*PanelFrame*"         style "panel"
widget_class "*PanelAppletFrame*"     style "panel-handle"

style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
    overlay_file    = "Panel/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "Panel/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"

---

