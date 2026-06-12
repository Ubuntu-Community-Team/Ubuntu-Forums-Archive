---
title: "GNOME toolbar icon size/style ignored in Oneiric (11.10)"
date: 2011-10-14
forum: Desktop Environments
---

### Post by rockdj on 2011-10-14
Previously in 11.04 and below, the /desktop/gnome/interface/toolbar_style and /desktop/gnome/interface/toolbar_icons_size settings were able to be used to control the toolbar within GNOME applications.  However, upon upgrading to 11.10, it seems these options are now being ignored, with the 'large' style toolbar being used with text beneath icons.  My toolbar_icons_size setting is currently on 'small-toolbar' and the toolbar_style is set as 'icons' -- which was working without trouble.

Have these settings moved somewhere else, or else, how can I get my toolbars back to small icons, without text?

Cheers.

---

### Post by crdlb on 2011-10-14
Yes, they have moved to GSettings/dconf, you can set them in dconf-editor at org.gnome.desktop.interface.

---

### Post by rockdj on 2011-10-14
> **crdlb said:**
> Yes, they have moved to GSettings/dconf, you can set them in dconf-editor at org.gnome.desktop.interface.

Excellent, thanks.  The toolbar-style setting takes effect but setting the toolbar-icons-size to 'small' has no effect (both large and small are the same -- 32px size [at a guess?]).

Should this be taking effect, or it is overridden somewhere else?  I've logged in/out and restarted the computer but no difference.

---

### Post by crdlb on 2011-10-14
> **rockdj said:**
> Excellent, thanks.  The toolbar-style setting takes effect but setting the toolbar-icons-size to 'small' has no effect (both large and small are the same -- 32px size [at a guess?]). It looks like small is 18x18 and large is 24x24. Perhaps it doesn't work because there are no 18x18 icons in your icon theme.

---

### Post by rockdj on 2011-10-16
> **crdlb said:**
> It looks like small is 18x18 and large is 24x24. Perhaps it doesn't work because there are no 18x18 icons in your icon theme.


Okay, but it seems extremely odd that none of the themes that came installed with Ubuntu 11.10 have 18x18 size icons when the small toolbar was fine back with 11.04.  That is unless Gnome changed its small toolbar size.

In any case, has anyone been able to use small toolbars in 11.10?

---

### Post by rockdj on 2012-03-01
Any updates about this?

---

### Post by rockdj on 2012-04-09
> **rockdj said:**
> Any updates about this?

Worked around using an answer from here: [http://askubuntu.com/questions/69576/how-to-customize-the-gnome-classic-panel](http://askubuntu.com/questions/69576/how-to-customize-the-gnome-classic-panel)

[INDENT] Reduce the size of the icons to 16 pixels
This will also reduce the height of the top panel from 30 to 24 pixels.

2a. Create folder for config files:

mkdir ~/.config/gtk-3.0
2b. Create or edit ~/.config/gtk-3.0/settings.ini and add this:

[Settings]
gtk-icon-sizes = panel-menu=16,16:gtk-large-toolbar=16,16[/INDENT]

Done for now.

---

### Post by rockdj on 2012-10-24
Just experienced a regression for this issue upon upgrading to Quantal (12.10).  The good news is that it's just a matter of moving this setting:

[INDENT]gtk-icon-sizes = panel-menu=16,16:gtk-large-toolbar=16,16[/INDENT]

into **/etc/gtk-3.0/settings.ini** (replacing the pre-existing **gtk-icon-sizes** setting) and you're golden.  

Seems as though the configuration file in **~/.config/gtk-3.0/settings.ini** is no longer considered. As per [http://developer.gnome.org/gtk3/3.2/GtkSettings.html](http://developer.gnome.org/gtk3/3.2/GtkSettings.html), the two locations (/etc/gtk-3.0 and $XDG_CONFIG_HOME/gtk-3.0) are considered.  On my 12.10 system, I don't have a XDG_CONFIG_HOME env variable set (anymore?) so this might be why.

At any rate, this fixes the issue.

---

### Post by chraazy on 2013-05-21
Hello,

I'm having some issue with this. I tried the steps mentioned above but I am unable to get the toolbar in Rhythmbox to show only icons. No matter what I select in dconf (org.gnome.desktop.interface/toolbar style) it continues to show both icons and text vertically. Even if I choose both horizontally, it is still vertical. I'm using a fresh install of Ubuntu 13.04 and have tried rebooting and logging out/in after making changes. I was able to get the icon size to be small, but that wasn't my priority. I would like to remove the text from the toolbar so it shows only icons. I don't really care about this in all apps, just rhythmbox. Using the rhythmbox-ui.xml file under /usr/share/rhythmbox I was able to remove the seperators from the rhythmbox toolbar, but removing text is what I'm really wanting to do here. Any suggestions?

---

