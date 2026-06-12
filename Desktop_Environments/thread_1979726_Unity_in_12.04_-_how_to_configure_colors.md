---
title: "Unity in 12.04 - how to configure colors?"
date: 2012-05-14
forum: Desktop Environments
---

### Post by pbpersson on 2012-05-14
I just installed 12.04 and would like to configure my colors - such as the panel, the active title bar, the inactive title bar, the windows backgrounds, the icons, etc.

However, I cannot find where to accomplish this.  I have looked at several articles.  Some said to use "System settings" but it was not there.  There is an appearance icon but it does not change the colors.  Then I tried "My Unity" but there is no way to set the colors there, all I found was how to select a few themes.  One article said to use Compiz Configuration Settings Manager but then another said it will break your desktop. I went in there but did not find any color settings.  Then another article suggested I download some Gnome Color Settings widget but that did not seem to change the colors.  Yet another article suggested that I use the Gnome configuration editor to randomly change things in the registry without knowing what I was doing.

Can someone point me in the right direction?  I am really lost and going in circles.

---

### Post by pbpersson on 2012-05-15
bump?

---

### Post by LarsKongo on 2012-05-15
The colors are specified in the theme's CSS files.

Copy /usr/share/themes/*name of the theme you're using* to ~/.themes
Easiest way is to open a terminal and: (Using the default theme Ambiance in this example.)
```
cp -r /usr/share/themes/Ambiance ~/.themes
```
If you're using Unity and want to change the color of the panel, then open *~/.themes/Ambiance/gtk-3.0/apps/unity.css*

Find these lines:
```
UnityPanelWidget,
.unity-panel {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (@dark_bg_color, 1.5)),
                                     to (shade (@dark_bg_color, 1.04)));
    border-top-color: shade (@dark_bg_color, 1.6);
    border-style: solid;
    border-width: 1px 0 0 0;

    color: @dark_fg_color;

    -unico-border-gradient: none;
}
```

And for example change them to: (To get a bright panel.)

```
UnityPanelWidget,
.unity-panel {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (@bg_color, 1.15)),
                                     to (shade (@bg_color, 1.0)));
    border-top-color: #fff;
    border-style: solid;
    border-width: 1px 0 0 0;

    color: #000; /* Black text color */

    -unico-border-gradient: none;
}
```

For the active/inactive titlebar colors, look in:
~/.themes/Ambiance/metacity-1/metacity-theme-1.xml

For other general colors:
~/.themes/Ambiance/gtk-3.0/gtk.css

Note: For any change to take effect it requires you to log out and then login again.

---

### Post by Frogs Hair on 2012-05-15
The color change option in appearance preferences was removed when gnome 3 was released . Panel properties can only be accessed in Classic Gnome which allows for panel color change. Changing the theme CSS is the only way to change color at the moment without installing a different desktop environment.

---

### Post by pbpersson on 2012-05-15
> **Frogs Hair said:**
> The color change option in appearance preferences was removed when gnome 3 was released. 

I have been told so many times that the charm of Linux is that you are in control of your own environment unlike Windows where so many things are decided by Microsoft and you have to just accept and like what they decide for your life.

Is the direction of Linux changing?

---

### Post by pbpersson on 2012-05-15
> **LarsKongo said:**
> The colors are specified in the theme's CSS files.

Copy /usr/share/themes/*name of the theme you're using* to ~/.themes
Easiest way is to open a terminal and: (Using the default theme Ambiance in this example.)
```
cp -r /usr/share/themes/Ambiance ~/.themes
```
If you're using Unity and want to change the color of the panel, then open *~/.themes/Ambiance/gtk-3.0/apps/unity.css*

Find these lines:
```
UnityPanelWidget,
.unity-panel {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (@dark_bg_color, 1.5)),
                                     to (shade (@dark_bg_color, 1.04)));
    border-top-color: shade (@dark_bg_color, 1.6);
    border-style: solid;
    border-width: 1px 0 0 0;

    color: @dark_fg_color;

    -unico-border-gradient: none;
}
```

And for example change them to: (To get a bright panel.)

```
UnityPanelWidget,
.unity-panel {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (#f2f2f2, 1.0)),
                                     to (shade (#e2e2e2, 1.0)));
    border-top-color: #fff;
    border-style: solid;
    border-width: 1px 0 0 0;

    color: #000; /* Black text color */

    -unico-border-gradient: none;
}
```

For the active/inactive titlebar colors, look in:
~/.themes/Ambiance/metacity-1/metacity-theme-1.xml

For other general colors:
~/.themes/Ambiance/gtk-3.0/gtk.css

Note: For any change to take effect it requires you to log out and then login again.

Thank you, I will try those methods to change the colors.  This is a test machine so if I break something I....well, I guess I can save backups of any file I touch and fix it using the live CD. :)

---

### Post by qox on 2012-06-02
How about unity panel menus ?
I've changed every colors in unity.css and strangely it didnt affect the menus ...

---

### Post by mcduck on 2012-06-02
> **pbpersson said:**
> I have been told so many times that the charm of Linux is that you are in control of your own environment unlike Windows where so many things are decided by Microsoft and you have to just accept and like what they decide for your life.

Is the direction of Linux changing?

You are still in control, you just might need to do some work to do what you want instead of being able to just use a simple GUI tool for the purpose.

Having freedom doesn't mean that there would always be a simple and easy way to use your freedom. Actually, most of the things you are free to do with your Linux system don't have easy tools. (Besides, the developers of various programs also have the freedom to do things like they want to, in which case you still have the freedom to use some other program or desktop environment instead... ;))

(Anyway, the color configuration wasn't removed to prevent you from changing colors or anything like that, it's simply because the old tool only worked for GTK2, while Gnome is now using GTK3 and nobody has created a GUI tool for configuring GTK3 colors yet. And it actually took someting like 8 years before people figured out a way to do that with GTK2, it was one of the last things added to Gnome2 desktop, so it definitely wasn't a feature you should have taken for granted. Anyway, implementing that for GTK3 should be a bit easier, so hopefully we won't have to wait quite that long this time... :))

---

### Post by qox on 2012-06-02
Hey, I didnt bump that issue for an history lesson ! 
/joke

---

### Post by nll on 2012-06-02
You don't need to edit CSS files. You can easily change the colors of both the [Ambiance and Radiance themes]("http://www.webupd8.org/2012/01/ambiance-and-radiance-colors-theme-pack.html") and the [Humanity icons]("http://www.webupd8.org/2012/02/humanity-icons-colors-8-different.html") by using ppas.

---

### Post by fragos on 2012-06-03
To change theme colors there are three files you need to edit.

    /usr/share/themes/{theme name}/gtk-3.0/gtk.css
    /usr/share/themes/{theme name}/gtk-3.0/settings.ini
    /usr/share/themes/{theme name}/gtk-2.0/gtkrc

In the beginning of these files you'll find 4 pairs of core foreground and background colors used in applications based on the gtk 2 and gtk 3 libraries. Pair base_color and text_color are used for the document or text entry portions of windows where bg_color and fg_color are are used for the windows area where icons and labels are displayed. Selected pair is for selected text and the tooltip pair is used for the tips that pop up when you hover over a button or link. These colors may be applied by applications with varying opacity or shadings. The color of text in buttons comes from the fg_color. These sets of labels appear in all three files so I've been changing all three to be the same for any label I change. Here's an example of what I changed in the gtk.css file in the Ambiance theme.

    /* default color scheme */
    @define-color bg_color #cdc3b8;
    @define-color fg_color #262626;
    @define-color base_color #accdff;
    @define-color text_color #262626;
    @define-color selected_bg_color #01b9fc;
    @define-color selected_fg_color #ffffff;
    @define-color tooltip_bg_color #A3D0FF;
    @define-color tooltip_fg_color #023C79;

These colors are used globally sometimes with different degrees of opacity by application specific themes. The unity panel referenced above is one such example. Not all applications have been updated to use gtk 3.0, that is why you have to edit three files to get color changes to apply to all applications.

---

### Post by qox on 2012-06-04
@fragos , 
I've done that. But Unity panel's menu background color is still the same (default Ambiance I believe). Im talking about the top bar BTW, not the launcher.

Any idea where that code is ? I tried changing all colors in unity.css without success :(

---

### Post by fragos on 2012-06-04
I would have thought the title bar was a function of metacity but couldn't locate anything that seemed to be relative. My best guess is in /usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css but I can't see for sure that it is. Despite all the theme tweaking I've done I never tried changing the title bar. The MyUnity application provides for the changing of panel transparency. With 0 transparency you get the same dark color as the title bar. Increasing the transparency lets the color and shading of the wallpaper show through.

---

### Post by qox on 2012-06-04
Im talking about the menus of course (Files, Edit, View ... in the global menu) .. Same as applets' menus (calendar, me-menu ...).

It's OK I guess. It just differs from the right-click menus...

---

