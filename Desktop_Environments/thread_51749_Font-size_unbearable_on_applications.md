---
title: "Font-size unbearable on applications"
date: 2005-07-25
forum: Desktop Environments
---

### Post by AJKDiablo on 2005-07-25
I didn't have patience for checking if there is another topic that gives me the answer. I'm quite frustrated 'cause some of my applications look like this [screencapture](http://koti.mbnet.fi/ajkdiabl/xmule.png). Would truly appreciate help.

---

### Post by Who on 2005-07-25
Though you probably don't know it, the problem is caused by the fact that Linux has two major toolkits (sets of buttons, checkboxes, menus etc), one called GTK and the other based on QT from Trolltech. 
Judging from your screenshot, you are using a Gnome (or GTK, at least) app in KDE
Now, KDE uses a differnt one from Gnome (QT vs GTK), and so in KDE, gnome apps, by default, have the default theme (makes sense :P). 
In order to restore the Gnome apps (like the one pictured) you need to create two files in your home directory called .gtkrc and .gtkrc-2.0  with the following content

include "/usr/share/themes/Clearlooks-DeepSky/gtk-2.0/gtkrc"
gtk-font-name = "Bitstream Vera Sans 12" 

or something similar - you will see that you can edit certain things as you like - for example the fontsize, and which theme is being used...

you could've found this out from [http://ubuntu.guilinux.com/viewtopic.php?topic=321&forum=93](http://ubuntu.guilinux.com/viewtopic.php?topic=321&forum=93), which I got from google using gtk kde theme ubuntu as search words (it is about the 6th down. Often google is quicker than using the forums :)

This, I'm sure, is not the full story, but it should solve the problem you have. On previous distros I have copied entire gtkrc files from themes (/usr/share/themes/blahdeblahwhatever/gtkrc (I think, I'm not at home)) into the two locations in the home folder - which worked too...but I never understood the whole of the file, so I didn't really trust it :).

Hope that works, 

Who

---

### Post by AJKDiablo on 2005-07-25
the content of .gtkrc-2.0 looks like this:
[i]
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Sans Serif 12"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="Sans Serif 12"
[/i]

And it seems that there's no problems with qtk2. So far these programs have been causing the same problem: winetools, xmule, xmms

I ran apt-get dist-upgrade to ensure that the system is up to date. I tried to change font in xmms since but it did not work. I also tried to change the font from 
*control center -> appearance and themes -> gtk styles* and it did take effect to gtk2 programs. 


All help is still rather welcome.

---

