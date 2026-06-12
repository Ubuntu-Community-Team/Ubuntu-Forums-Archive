---
title: "gnome-color-chooser like utility for kde4?"
date: 2011-06-05
forum: Desktop Environments
---

### Post by 13east on 2011-06-05
With gnome-color-chooser you are able to tweak a lot visual aspects the gnome desktop.  

Is there anything similar for the kde desktop?

---

### Post by Frogs Hair on 2011-06-05
[http://www.kde.org/applications/graphics/kcolorchooser/](http://www.kde.org/applications/graphics/kcolorchooser/)

---

### Post by 13east on 2011-06-05
> **Frogs Hair said:**
> [http://www.kde.org/applications/graphics/kcolorchooser/](http://www.kde.org/applications/graphics/kcolorchooser/)

Nope... nothing similar... kcolorchooser is just a color pallete to let you pick custom color combinations...  description from the page you linked: > KColorChooser is a simple application to select the color from the screen or from a pallete.
Features

    Select colors from any location on the screen.
    Select colors from a range of standard palletes available.
    Color values shown in Hue-Saturation-Value (HSV), Red-Green-Blue (RGB) and HTML formats.

[Gnome-Color-Chooser]("https://launchpad.net/gnome-color-chooser"):
> GNOME Color Chooser is a program which allows you to modify the appearance of your GNOME desktop

Features:
-> change most important colors (e.g. background, window decoration, tooltips)
-> change sizes of widgets (e.g. of buttons, scrollbars or the main padding)
-> allow use of light-colored wallpapers without getting icons unreadable
-> adjust the size of start menues / panel menues / or large-toolbars
-> *new* colorize desktop icons and activate their new hover effects (requires GNOME 2.18+)
-> *new* configure your gtk engines and let your current theme be drawn by whatever gtk engine you want (requires GNOME 2.18+ or engines that support the newly introduced engine schema definitions respectively)
-> many more, of course, heh ;-)

---

### Post by ankspo71 on 2011-06-05
Hi,
I don't think there is a KDE equivalent to gnome-color-chooser, but there are some theme related things in Kubuntu that can be tweaked (or edited) away. For instance you can run the command oxygen-settings to change some hidden options for the Oxygen theme style and it's effects. [http://hugo-kde.blogspot.com/2010/06/oxygen-settings.html](http://hugo-kde.blogspot.com/2010/06/oxygen-settings.html)

If you install the package called qtcurve, you will be installing a theme style that you can customize with a ton of configuration options. You can choose the colors, border options, window button shapes and colors, gradients, transparency, shadows, application background image, progressbars and scrollbars, and more. 

Hope this helps.

---

### Post by 13east on 2011-06-05
> **ankspo71 said:**
> Hi,
I don't think there is a KDE equivalent to gnome-color-chooser, but there are some theme related things in Kubuntu that can be tweaked (or edited) away. For instance you can run the command oxygen-settings to change some hidden options for the Oxygen theme style and it's effects. [http://hugo-kde.blogspot.com/2010/06/oxygen-settings.html](http://hugo-kde.blogspot.com/2010/06/oxygen-settings.html)

If you install the package called qtcurve, you will be installing a theme style that you can customize with a ton of configuration options. You can choose the colors, border options, window button shapes and colors, gradients, transparency, shadows, application background image, progressbars and scrollbars, and more. 

Hope this helps.

Thx for your help.
Will Try.

---

### Post by 13east on 2011-06-05
> **ankspo71 said:**
> ...If you install the package called qtcurve, you will be installing a theme style that you can customize with a ton of configuration options. You can choose the colors, border options, window button shapes and colors, gradients, transparency, shadows, application background image, progressbars and scrollbars, and more...

- the qtcurve theme is very nice in all aspects expect the look of the title-bar; the color and text combo makes them nearly unreadable.

1) is there way to incorperate the looks from the title-bar of a different theme? i.e. [Radial Aurorae]("http://opendesktop.org/content/show.php?content=115838")

OR

2) is there any way to just make changes to the title-bar background and foreground color?

---

### Post by ankspo71 on 2011-06-05
Hi,
Go to System Settings, Application Appearance, Colors, now the "colors" tab, then in the 'common colors' color set, change the colors to these:
Active Titlebar
Active Titlebar Text
Inactive Titlebar
Inactive Titlebar Text

Also, sometimes I have to restart the system for the qtcurve titlebars to look right. 

Aurorae window border themes are made for KDE so you shouldn't have any problem using those. Go to System Settings, Workspace Appearance, Window Decorations, click on the Get New Window Decorations button, and search for Radial Aurorae in the search box. Then install Radial Aurorae by clicking on the install button. After it is installed, select Radial Aurorae from the preview window and click apply.

Hope this helps.

---

### Post by 13east on 2011-06-05
> **ankspo71 said:**
> Hi,
Go to System Settings, Application Appearance, Colors, now the "colors" tab, then in the 'common colors' color set, change the colors to these:
Active Titlebar
Active Titlebar Text
Inactive Titlebar
Inactive Titlebar Text

Also, sometimes I have to restart the system for the qtcurve titlebars to look right...

thx... will try this.

> **ankspo71 said:**
> ...Aurorae window border themes are made for KDE so you shouldn't have any problem using those. Go to System Settings, Workspace Appearance, Window Decorations, click on the Get New Window Decorations button, and search for Radial Aurorae in the search box. Then install Radial Aurorae by clicking on the install button. After it is installed, select Radial Aurorae from the preview window and click apply.

Hope this helps.

What I was looking for was to mix and match two different themes?  I wanted to use the title-bar from Aurorae w/ qtcurve theme with all of its available settings.

---

### Post by ankspo71 on 2011-06-05
Hi Again,
You might already have found out about this, but I probably should have mentioned that you can customize the qtcurve theme settings, and import new qtcurve themes, by going to System Settings, Application Appearance, Style, then click on the configure button next to where you have selected qtcurve as your style.

You can apply qtcurve's own window border by going to System Settings, Workspace Appearance, Window Decorations, then select the qtcurve window border.

Also, qtcurve works nicely with GTK applications (including firefox), but you have to apply the qtcurve style separately by going to... System Settings, Application Appearance, GTK+ Appearance, then choose qtcurve for "GTK widget style:".

---

### Post by ankspo71 on 2011-06-05
> **13east said:**
> 
What I was looking for was to mix and match two different themes?  I wanted to use the title-bar from Aurorae w/ qtcurve theme with all of its available settings.

The Aurorae window decorations can be used with (and work well with) qtcurve themes, but as far as changing the titlebar background of the Aurorae window decoration you would have to edit the image files yourself with Inkscape or Karbon (since it relies on images). Other than that, you will still be able to use qtcurve's settings.

The qtcurve window decoration doesn't rely on images, so the color can be changed in system settings.

---

