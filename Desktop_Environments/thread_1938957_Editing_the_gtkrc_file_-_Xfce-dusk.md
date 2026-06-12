---
title: "Editing the gtkrc file - Xfce-dusk"
date: 2012-03-10
forum: Desktop Environments
---

### Post by sirriffsalot on 2012-03-10
Hello!

   I'm using the Xfce-dusk theme, and I'm so close to getting it right how I want it, but there's ONE thing I can't manage to do. I am sure I am simply overlooking something obvious, but I'm getting to annoyed to keep looking.

   What I basically want is for all the window borders to have their orange text, but the only problem is that the active or selected window I am at always turns it's text to white, and for the life of me I can't find the text where I tell it to do do this.. Any suggestions?

   Thanks for reading :)

   --> Leo

---

### Post by Toz on 2012-03-10
xfce themes are made up of two components: the Appearance theme (set in SettingsManager->Appearance->Style) and the Window Manager theme (set in SettingsManager->WindowManager->Style).

The theme files are located in /usr/share/themes/<theme_name>. The settings for the Appearance style are located in the gtk-2.0/gtkrc file and the settings for the WindowManager style are located in xfwm4/themerc file.

For the Xfce-dusk theme, there is only an Appearance style. Therefore you must be using some other WindowManager style. Its possible that the configuration setting that you are looking for is one of those two locations. Unfortunately, from your description, I can not tell if you are referring to the Appearance or Window Manager style. When I set my Appearance style to Xfce-dusk, I do not see an orange colour. 

Would it be possible to include a screenshot and identify the Window Manager style that you are using?

---

### Post by sirriffsalot on 2012-03-10
Aah, I see.

Thing is I have been editing the Xfce-dusk theme to be more to my liking. My window manager settings are at the default.

However the problem is simply, and a rather picky one I know, that whatever selected window I have turns its border text color to white. The settings as they are don't bother me, but it bothers me that I can't figure out how to change it, haha:) I've been to every "default" file that has any configurable code in it, and changed the "#ffffff" in every "active_text_color=#ffffff" I could find, but to no avail, and yes I re-selected the "defaul" window option with every change.. What am I missing?:)

I could use another window theme to make it easier to find the right file (there are five folders with the name "default", four of them with numberings such as "-4.0"), but I prefer the looks of the "default" so it would be great to figure out how to change the settings of that one!

Thanks for taking the time, and sorry if my writing is sloppy - tired! ;D

--> Leo

---

### Post by Toz on 2012-03-10
Ok. If I understand correctly, have a look at the file **/usr/share/themes/Default/xfwm4/themerc**. The first setting:
> active_text_color=#ffffff
...I believe is the one you want to change.

---

### Post by sirriffsalot on 2012-03-12
My man! Exactly what I wanted:) Changed it to what I preferred and active window changed to that color!

Now that we're at it though...^^ Seems you have quite the knowledge involving these things, here's another one for you if you're interested, haha:) The scroll bar on my windows are slightly uneven, to such an extend that I have to carefully hover over the whole bar in order to see a scroll bar react. Usually I just use my ... uhm, what's it called haha, rollerthing on my mouse:$ ... but at times it would be handy to be able to left-click + hold-scroll it around.

So, if that was incomprehensible; how would I go about making these two things contrast more: the scrolling bar on windows and the bar in which it resides:) Right now they background is black and the bar is slightly more gray but difficult to spot none the less, so I suppose it has been be going crazy pasting "#000000" everywhere, but if you could save me time that'd be lovely!

Cheers!:)

Edit: Also, in the type fields of for instance starting a taskmanager in sudo, the marker for where I am at is also black, or I suppose it is haha, so I can't see it obviously since the background also is black. This too would be a cool thing to fix:) Thanks a lot!

---

### Post by Toz on 2012-03-12
> **LeoTB said:**
> My man! Exactly what I wanted:) Changed it to what I preferred and active window changed to that color!
Good news.

> Now that we're at it though...^^ Seems you have quite the knowledge involving these things, here's another one for you if you're interested, haha:) The scroll bar on my windows are slightly uneven, to such an extend that I have to carefully hover over the whole bar in order to see a scroll bar react. Usually I just use my ... uhm, what's it called haha, rollerthing on my mouse:$ ... but at times it would be handy to be able to left-click + hold-scroll it around.

So, if that was incomprehensible; how would I go about making these two things contrast more: the scrolling bar on windows and the bar in which it resides:) Right now they background is black and the bar is slightly more gray but difficult to spot none the less, so I suppose it has been be going crazy pasting "#000000" everywhere, but if you could save me time that'd be lovely!

Cheers!:)
The easiest way will be to override the settings in that theme by creating a **.gtkrc-2.0** file in your home directory with the following content:
```

style "theme-scrollbar" {
    bg[ACTIVE]        = "#003263"
    bg[INSENSITIVE]   = "#303030"
    bg[NORMAL]        = "#232323"
    bg[PRELIGHT]      = "#003263"
    bg[SELECTED]      = "#002849"
}
class "GtkScrollbar"   style "theme-scrollbar"

```
...and edit those values to suit. You will need to change the theme away and back to Xfce-dusk to see the differences. 
NOTE: These changes will affect all themes. If you change your theme, make sure to comment out these settings.

> Edit: Also, in the type fields of for instance starting a taskmanager in sudo, the marker for where I am at is also black, or I suppose it is haha, so I can't see it obviously since the background also is black. This too would be a cool thing to fix:) Thanks a lot!
The default is white. Did you change it? Could you post a screenshot?

---

### Post by sirriffsalot on 2012-03-13
Perfect solution once again for the scroll bar, I've got another similar issue I forgot to include though; the VLC player also has a very dark look, naturally, and the problem is basically the same, in which the "counter" or whatever it is called that displays where you're at in a song or video is just as dark as the background and can barely be spotted thanks to the black line it runs on. 

Also, haha, when I mouse over certain places, such as in VLC where it is supposed to display additional information if you leave the mouse there long enough, an entirely white square will appear so I can't actually see the info, lol:) Ideas?:) The second problem I suppose I can figure out myself by changing any "FFFFFF" that I see in what I configured before I posted this thread, and see which one it is, so no worries if you don't know!

As for the screen-shot, I really have no idea how I could pull that off, because when I am prompted to type in a password for root privileges in nautilus, the rest of the screen naturally freezes, and I can't take a screen-shot without closing it. Perhaps you misunderstood, it is the rectangle box I am prompted to that has it's marker also in black, or so I would presume since I can't see it. So when I type the figures appear but with no "marker" around:P

---

### Post by Toz on 2012-03-13
> **LeoTB said:**
> Perfect solution once again for the scroll bar,
Good to hear
> I've got another similar issue I forgot to include though; the VLC player also has a very dark look, naturally, and the problem is basically the same, in which the "counter" or whatever it is called that displays where you're at in a song or video is just as dark as the background and can barely be spotted thanks to the black line it runs on. 
Add the following code to your ~/.gtkrc-2.0 file:
```

style "theme-range" {
    bg[ACTIVE]        = "#003263"
    bg[INSENSITIVE]   = "#303030"
    bg[NORMAL]        = "#003263"
    bg[PRELIGHT]      = "#003263"
    bg[SELECTED]      = "#002849"
}
class "GtkRange"   style "theme-range"

```
...and edit the values to suit. Note, these values will affect all scroll bars.

> Also, haha, when I mouse over certain places, such as in VLC where it is supposed to display additional information if you leave the mouse there long enough, an entirely white square will appear so I can't actually see the info, lol:) Ideas?:) The second problem I suppose I can figure out myself by changing any "FFFFFF" that I see in what I configured before I posted this thread, and see which one it is, so no worries if you don't know!
This one has something to do with the tooltip widget. Don't know off-hand, but let me look around and see what I can find.

> As for the screen-shot, I really have no idea how I could pull that off, because when I am prompted to type in a password for root privileges in nautilus, the rest of the screen naturally freezes, and I can't take a screen-shot without closing it. Perhaps you misunderstood, it is the rectangle box I am prompted to that has it's marker also in black, or so I would presume since I can't see it. So when I type the figures appear but with no "marker" around:P
I see. Have a look at the /usr/share/themes/Xfce-dusk/gtk-2.0/gtkrc file. There are 4 settings in the first section:
```
    GtkEntry::cursor_color                       = "#fcfcfc"
    GtkEntry::secondary_cursor_color             = "#fcfcfc"
    GtkTextView::cursor_color                    = "#fcfcfc"
    GtkTextView::secondary_cursor_color          = "#fcfcfc"

```
I think you may have changed them to #000000. Their default values are #fcfcfc and they will display the cursor in a more lighter colour.

---

### Post by Toz on 2012-03-14
Here is the code to change the tooltip. Add it to the end of your ~/.gtkrc-2.0 file and edit the values as required:
```

style "TOOLTIP" = "default" {
    bg[NORMAL] = "#FF0000"
    fg[NORMAL] = "#1F1F1F"
}
widget "*gtk-tooltip*" style:highest "TOOLTIP"

```

---

### Post by sirriffsalot on 2012-03-15
Once again your help is flawless:) However it does not affect the VLC "counter" problem... Ideas?:)

---

### Post by Toz on 2012-03-15
Perhaps I'm misunderstanding what the VLC "counter" is. I'm assuming its the horizontal slider that moves when the movie plays to indicate its location in the movie. 

According to this image: [http://www.freepenguin.it/immagini/vlc-screen1.png]("http://www.freepenguin.it/immagini/vlc-screen1.png"), is it the horizontal slider that sits between the movie and the status bar at the bottom?

---

### Post by sirriffsalot on 2012-03-16
Yes, precisely that. Only difficulty is that the slider is in camouflage with the "xfce4-dusk"'s window background color (black/dark-grey)...

---

### Post by sirriffsalot on 2012-03-23
bump^^

---

### Post by Toz on 2012-03-23
Sorry for the delay. I haven't been able to find a way to accurately make those changes. Then I came across this thread: [http://crunchbanglinux.org/forums/topic/119/theming-vlc-and-other-qt4-applications-under-openbox/]("http://crunchbanglinux.org/forums/topic/119/theming-vlc-and-other-qt4-applications-under-openbox/"). I think this might be related to the fact that vlc is based on qt, not gtk. By making the changes referenced in that thread to my ~/.config/Trolltech.conf file, I was able to change the colours. Perhaps the answer lies in the settings in that file?

---

### Post by sirriffsalot on 2012-03-29
Your time mate, no need for apology!

I can't find any such file in my home directory, the "Trolltech.conf" file is located in /etc/xdg and what's in the file is only 

[qt]
4.7\libraryPath=/usr/lib/kde4/plugins

So... What are we missing here?:)

---

### Post by Toz on 2012-03-29
If it exists, it would be located in ~/.config. If it doesn't exist, try creating it with the following content:
```

[Qt]
customColors\0=4280690214
customColors\1=4284374622
customColors\2=4294967295
customColors\3=4280690214
customColors\4=4294967295
customColors\5=4294967295
customColors\6=4294967295
customColors\7=4294967295
customColors\8=4294967295
customColors\9=4294967295
customColors\10=4294967295
customColors\11=4294967295
customColors\12=4294967295
customColors\13=4294967295
customColors\14=4294967295
customColors\15=4294967295
font="Sans Serif,9,-1,5,50,0,0,0,0,0"
Palette\active=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\inactive=#d1d1d1, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\disabled=#808080, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #808080, #ffffff, #808080, #5e5e5e, #5e5e5e, #000000, #262626, #808080, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
fontPath=@Invalid()
embedFonts=true
style=Plastique
doubleClickInterval=400
cursorFlashTime=1000
wheelScrollLines=3
resolveSymlinks=false
globalStrut\width=0
globalStrut\height=0
useRtlExtensions=false
XIMInputStyle=On The Spot
audiosink=Auto
videomode=Auto
GUIEffects=none
Font%20Substitutions\arial=helvetica
Font%20Substitutions\courier%20new=courier
Font%20Substitutions\sans%20serif=helvetica
Font%20Substitutions\times%20new%20roman=times
filedialog="@ByteArray(\0\0\0\xbe\0\0\0\x3\0\0\0\x1e\0\0\0\xff\0\0\0\0\0\0\0\x2\0\0\0^\0\0\x1x\x1\0\0\0\x6\x1\0\0\0\x1\0\0

```

---

### Post by sirriffsalot on 2012-03-30
Haha, I looked for the trolltech file in the home directory, not in the .config file in my home folder. The Trolltech.conf jolly-well does exist there!

This worked perfectly, once again! To lay the cherry on top of the ice-cream, would you mind explaining how to edit the colors? Having difficulty understanding where in that huge text that would be, seems like there are several places.

Thanks again for amazing help!:)

---

### Post by sirriffsalot on 2012-03-30
Never mind that, figured things out:)

Except one thing. In the standard VLC interface, if you go for My Computer and Music, it'll list in columns what is in that folder. Currently it is annoyingly enough listing every second file in white highlight, making it very difficult to read what the file is actually called. What do I have to edit in order to make those highlighted in black as well? Can't find it..

Cheers, once again:)

---

### Post by Toz on 2012-04-01
Hmmm. I'm not getting that here. Can you post back the contents of your ~/.config/Trolltech.conf and /usr/share/themes/Xfce-dusk/gtk-2.0/gtkrc files? I'll add them to my system and see if I get a similar effect.

---

### Post by sirriffsalot on 2012-04-02
Sure thing! Thanks once again:)

Here's the Xfce-dusk file:

style "default"
{
    GtkButton::default_border                    = {0, 0, 0, 0}
    GtkButton::default_outside_border            = {0, 0, 0, 0}
    GtkButton::child_displacement_x              = 0
    GtkButton::child_displacement_y              = 1
    GtkButton::default_spacing                   = 4
    GtkButton::focus-padding                     = 0
    GtkCheckButton::indicator_size               = 8
    GtkMenuBar::internal-padding                 = 1
    GtkMenuBar::shadow_type                      = out
    GtkHandleBox::shadow_type                    = out
    GtkMenuItem::selected_shadow_type            = etched-in
    GtkPaned::handle_full_size                   = 1
    GtkPaned::handle_size                        = 4
    GtkRadioButton::indicator_size               = 10
    GtkRange::slider_width                       = 12
    GtkRange::stepper_size                       = 10
    GtkRange::stepper_spacing                    = 0
    GtkRange::trough_border                      = 0
    GtkScrollbar::has_backward_stepper           = 1
    GtkScrollbar::has_secondary_backward_stepper = 0
    GtkScrollbar::min_slider_length              = 10
    GtkToolbar::shadow_type                      = out
    GtkWidget::focus-line-width                  = 1
    GtkWidget::focus_padding                     = 1 
    GtkWidget::interior_focus                    = 1 
    GtkWidget::internal_padding                  = 2 
    GtkEntry::cursor_color                       = "#fcfcfc"
    GtkEntry::secondary_cursor_color             = "#fcfcfc"
    GtkTextView::cursor_color                    = "#fcfcfc"
    GtkTextView::secondary_cursor_color          = "#fcfcfc"
    GtkEntry::cursor_aspect_ratio                = 0.1
    GtkEntry::cursor_aspect_ratio                = 0.1
    
    xthickness             = 1
    ythickness             = 1


    base[ACTIVE]      = "#ffffff"
    base[INSENSITIVE] = "#ffffff"
    base[NORMAL]      = "#000000"
    base[PRELIGHT]    = "#ff8c00"
    base[SELECTED]    = "#0000ff"

    bg[ACTIVE]        = "#151515"
    bg[INSENSITIVE]   = "#303030"
    bg[NORMAL]        = "#232323"
    bg[PRELIGHT]      = "#003263"
    bg[SELECTED]      = "#002849"

    fg[ACTIVE]        = "#dadada"
    fg[INSENSITIVE]   = "#151515"
    fg[NORMAL]        = "#ffffff"
    fg[PRELIGHT]      = "#fcfcfc"
    fg[SELECTED]      = "#fcfcfc"

    text[ACTIVE]      = "#ff8c00"
    text[INSENSITIVE] = "#ff8c00"
    text[NORMAL]      = "#ff8c00"
    text[PRELIGHT]    = "#ff8c00"
    text[SELECTED]    = "#ff8c00"

    engine "xfce" 
    {
	smooth_edge = true
        boxfill
        {
            fill_style = plain
        }
    }
}
widget_class "*"                   style "default"

style "menustyle" = "default"
{
    xthickness = 2
    ythickness = 2
}
widget_class "*BonoboDockItem"     style "menustyle"
class "*BonoboDockItem"            style "menustyle"
widget_class "*ToolBar"            style "menustyle"
class "*ToolBar"                   style "menustyle"
widget_class "*MenuBar"            style "menustyle"
class "*MenuBar"                   style "menustyle"

style "button" = "default"
{
    xthickness = 2
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = none
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.25
            shade_end = 1.00
        }
    }
}
widget_class "*Button*"            style "button"
class "*Button*"                   style "button"
widget_class "*button*"            style "button"
class "*button*"                   style "button"
widget_class "*OptionMenu*"        style "button"
class "*OptionMenu*"               style "button"
# widget_class "*Tree*"            style "button"
# class "*Tree*"                   style "button"
# widget_class "*GtkScale*"        style "button"
# class "*GtkScale*"               style "button"

style "sbstyle" = "default"
{
    xthickness = 2
    ythickness = 2
    engine "xfce" 
    {
        smooth_edge = true
        grip_style = none
        boxfill
        {
            fill_style = gradient
            orientation = automatic
            shade_start = 1.25
            shade_end = 1.00
        }
    }
}
widget_class "*Scrollbar*"         style "sbstyle"
class "*Scrollbar*"                style "sbstyle"
widget_class "*GtkScale*"          style "sbstyle"
class "*GtkScale*"                 style "sbstyle"

style "progress" = "default"
{
    xthickness = 2
    ythickness = 2
}
widget_class "*GtkProgress*"       style "progress" 
class "*GtkProgress*"              style "progress" 

style "menuitem" = "default"
{
    xthickness = 1
    ythickness = 2
}

widget_class "*MenuItem*"          style "menuitem"
class "*MenuItem*"                 style "menuitem"

style "flat" = "default"
{
    xthickness = 2
    ythickness = 2
}
widget_class "*HandleBox"         style "flat"

# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar"
{
    bg[SELECTED]      = "#000000"
    fg[SELECTED]      = "#ff8c00"
    bg[INSENSITIVE]   = "#000000"
    fg[INSENSITIVE]   = "#ff8c00"
}
widget "xfwm"                      style "titlebar"
class "MetaFrames"                 style "titlebar"
widget_class "MetaFrames"          style "titlebar"

style "pager" = "default"
{
    bg[NORMAL]        = "#000000"	# background colour
    bg[PRELIGHT]      = "#ff8c00"	# foreground colour on hover
    bg[SELECTED]      = "#3300CC"	# foreground colour
}
widget_class "*Pager*"             style "pager"
class "*Pager*"                    style "pager"

And here's the Trolltech.conf file

[Qt]
customColors\0=4280690214
customColors\1=4284374622
customColors\2=4294967295
customColors\3=4280690214
customColors\4=4294967295
customColors\5=4294967295
customColors\6=4294967295
customColors\7=4294967295
customColors\8=4294967295
customColors\9=4294967295
customColors\10=4294967295
customColors\11=4294967295
customColors\12=4294967295
customColors\13=4294967295
customColors\14=4294967295
customColors\15=4294967295
font="Sans Serif,9,-1,5,50,0,0,0,0,0"
Palette\active=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\inactive=#d1d1d1, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\disabled=#808080, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #808080, #ffffff, #808080, #5e5e5e, #5e5e5e, #000000, #262626, #808080, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
fontPath=@Invalid()
embedFonts=true
style=Plastique
doubleClickInterval=400
cursorFlashTime=1000
wheelScrollLines=3
resolveSymlinks=false
globalStrut\width=0
globalStrut\height=0
useRtlExtensions=false
XIMInputStyle=On The Spot
audiosink=Auto
videomode=Auto
GUIEffects=none
Font%20Substitutions\arial=helvetica
Font%20Substitutions\courier%20new=courier
Font%20Substitutions\sans%20serif=helvetica
Font%20Substitutions\times%20new%20roman=times
filedialog="@ByteArray(\0\0\0\xbe\0\0\0\x3\0\0\0\x1e\0\0\0\xff\0\0\0\0\0\0\0\x2\0\0\0\x64\0\0\xe\0\x1\0\0\0\x6\x1\0\0\0\x1\0\0\0\x3\0\0\0\x5\x66ile:\0\0\0\x19\x66ile:///home/sirriffsalot\0\0\0\"file:///home/sirriffsalot/Qtractor\0\0\0\x6\0\0\0J\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0/\0i\0\x64\0\x65\0\x65\0r\0.\0q\0t\0r\0\0\0V\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0M\0u\0s\0i\0\x63\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0/\0i\0\x64\0\x65\0\x65\0r\0.\0q\0t\0r\0\0\0h\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0M\0u\0s\0i\0\x63\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0/\0T\0\x65\0s\0t\0i\0n\0g\0 \0s\0h\0i\0t\0 \0\x32\0.\0q\0t\0r\0\0\0T\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0M\0u\0s\0i\0\x63\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0/\0z\0\x64\0s\0\x62\0.\0q\0t\0r\0\0\0p\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0M\0u\0s\0i\0\x63\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0/\0T\0\x65\0s\0t\0i\0n\0g\0,\0_\0t\0\x65\0s\0t\0i\0\x63\0l\0\x65\0s\0.\0q\0t\0r\0\0\0\x36\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0\0\0\x36\0/\0h\0o\0m\0\x65\0/\0s\0i\0r\0r\0i\0\x66\0\x66\0s\0\x61\0l\0o\0t\0/\0Q\0t\0r\0\x61\0\x63\0t\0o\0r\0\0\0~\0\0\0\xff\0\0\0\0\0\0\0\x1\0\0\0\0\0\0\0\0\x1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\x1\xf7\0\0\0\x4\x1\x1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\x64\xff\xff\xff\xff\0\0\0\x81\0\0\0\0\0\0\0\x4\0\0\x1\x4\0\0\0\x1\0\0\0\0\0\0\0\x41\0\0\0\x1\0\0\0\0\0\0\0\x41\0\0\0\x1\0\0\0\0\0\0\0q\0\0\0\x1\0\0\0\0\0\0\0\x1)"

[Qt%20Plugin%20Cache%204.7.false]
usr\lib\i386-linux-gnu\qt4\plugins\inputmethods\libqimsw-multi.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\kde4\plugins\imageformats\kimg_dds.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:20
usr\lib\kde4\plugins\imageformats\kimg_eps.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_exr.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_jp2.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_pcx.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_pic.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_psd.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_ras.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_rgb.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_tga.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_xcf.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\kde4\plugins\imageformats\kimg_xview.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T22:31:21
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqgif.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqico.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqjpeg.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqmng.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqsvg.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:43
usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqtiff.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:42
usr\lib\i386-linux-gnu\qt4\plugins\iconengines\libqsvgicon.so=40704, 0, i386 linux g++-4 full-config, 2012-01-13T23:16:43

[Qt%20Factory%20Cache%204.7]
com.trolltech.Qt.QInputContextFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\inputmethods\libqimsw-multi.so=2012-01-13T23:16:42, imsw-multi
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_dds.so=2012-01-13T22:31:20, dds
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_eps.so=2012-01-13T22:31:21, eps, EPS, epsi, EPSI, epsf, EPSF
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_exr.so=2012-01-13T22:31:21, exr, EXR
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_jp2.so=2012-01-13T22:31:21, jp2
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_pcx.so=2012-01-13T22:31:21, pcx, PCX
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_pic.so=2012-01-13T22:31:21, pic
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_psd.so=2012-01-13T22:31:21, psd, PSD
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_ras.so=2012-01-13T22:31:21, ras, RAS
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_rgb.so=2012-01-13T22:31:21, rgb, RGB, rgba, RGBA, bw, BW, sgi, SGI
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_tga.so=2012-01-13T22:31:21, tga, TGA
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_xcf.so=2012-01-13T22:31:21, xcf, XCF
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\kde4\plugins\imageformats\kimg_xview.so=2012-01-13T22:31:21, xv
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqgif.so=2012-01-13T23:16:42, gif
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqico.so=2012-01-13T23:16:42, ico
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqjpeg.so=2012-01-13T23:16:42, jpeg, jpg
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqmng.so=2012-01-13T23:16:42, mng
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqsvg.so=2012-01-13T23:16:43, svg, svgz
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\imageformats\libqtiff.so=2012-01-13T23:16:42, tiff, tif
com.trolltech.Qt.QIconEngineFactoryInterfaceV2%3A\usr\lib\i386-linux-gnu\qt4\plugins\iconengines\libqsvgicon.so=2012-01-13T23:16:43, svg, svgz, svg.gz
com.trolltech.Qt.QIconEngineFactoryInterface%3A\usr\lib\i386-linux-gnu\qt4\plugins\iconengines\libqsvgicon.so=2012-01-13T23:16:43

Have fun^^

---

### Post by Toz on 2012-04-03
With these files, I can't replicate the issue. Perhaps its something in your ~/.gtkrc-2.0 file. Could you post it?

BTW, it would be easier to read if you posted the files back using code tags. See the CODE section of this link ([http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")) for information on how.

---

### Post by sirriffsalot on 2012-04-04
```


style "theme-scrollbar" {
    bg[ACTIVE]        = "#000000"
    bg[INSENSITIVE]   = "#000000"
    bg[NORMAL]        = "#ff8c00"
    bg[PRELIGHT]      = "#FF8C00"
    bg[SELECTED]      = "#000000"
}
class "GtkScrollbar"   style "theme-scrollbar"

style "TOOLTIP" = "default" {
    bg[NORMAL] = "#FF0000"
    fg[NORMAL] = "#1F1F1F"
}
widget "*gtk-tooltip*" style:highest "TOOLTIP"


```

:)

---

### Post by Toz on 2012-04-04
Hmmm. I'm still not seeing it. Here is what I get:

---

### Post by sirriffsalot on 2012-04-06
Well, what I meant was, when you open VLC (the standard graphical interface), and you have these > selections for "My Computer", "Devices", "My Videos" et cetera; if you double click on them and get deep into a bunch of files, with my settings this annoying display appears. Can't find out how add a screenshot, so if this doesn't make sense to you, please show me how! :-)

--> Leo

---

### Post by Toz on 2012-04-07
> **LeoTB said:**
> Can't find out how add a screenshot, so if this doesn't make sense to you, please show me how! :-)

--> Leo
Click on the reply button then the "Advanced" button. In this view, there is an icon for attachements (paper clip). Click on it and a window will open that will allow you to add a screenshot.

---

### Post by sirriffsalot on 2012-04-07
Cheers:)

---

### Post by Toz on 2012-04-07
It's the media browser and I get the same effect. It turns out that the 17th value in the Palette\inactive line controls the lighter color. I changed it to #565656 and it looks much more pleasant.
```

Palette\inactive=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #565656, #000000, #ffffdc, #000000
```

EDIT: Colours change again when you click on the files. Looks like you have to change both the Palette\active and Palette\inactive lines:
```

Palette\active=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #565656, #000000, #ffffdc, #000000
Palette\inactive=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #565656, #000000, #ffffdc, #000000
```

---

### Post by sirriffsalot on 2012-04-08
Once again, impeccable assistance. Thanks another million, Toz! Hopefully the quantities of thanks do not reduce the significant emphasis of each!

---

