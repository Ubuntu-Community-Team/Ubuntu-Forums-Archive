---
title: "(old story coming back) : GTK applications in KDE4 have a bad, unchangeable theme"
date: 2010-01-26
forum: Desktop Environments
---

### Post by michaelmestre on 2010-01-26
I have just installed Ubuntu 9.10 and downloaded all the updates.
I installed manually KDE4 from synaptic, and it seems to be working fine.

However, GTK applications always have the 'default look' in KDE, albeit with a huge font. This problem does not exit in a Gnome session.
 I tried to change this by downloading the GTK appearance configurator for KDE (it shows up as 'GTK+ appearance' in the Appearance settings of the KDE system settings). This has no effect on the look of the GTK applications. 
I tried to delete all the .gtkrc* files in my home directory, but still no effect.  

Do you have any ideas how I can fix this ? I should add that my home partition comes from a Hardy installation, so there may be configuration files for GTK or Gnome that interfere with the layout. 


 Thank you ! Michael

---

### Post by Zorael on 2010-01-26
Well, you need the **gtkrc-2.0-kde4** file in your home directory, and the **gtk2-engines-qtcurve.rc.sh** script in **~/.kde/env** to export it upon login. I think the GTK+ Appearance dialog should create these for you, but if you removed either I think you'd get funky results.
```
$ cat .gtkrc-2.0-kde4
**include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"**

$ cat .kde/env/gtk2-engines-qtcurve.rc.sh
[B]#!/bin/bash


# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4[/B]
```

You might want to rename or remove any **~/.fonts.conf** file if you're getting font weirdness, too. Applying font settings in Appearance -> Fonts should create a new one with the settings you specify there. Not all GTK apps know to listen to KDE's settings, at which point most fall back to fontconfig (for which ~/.fonts.conf is your user-specific settings).

Failing that, I think we'd need to see some screenshots of how it looks.

---

### Post by michaelmestre on 2010-01-26
Hi,   Thank you for your answer. The second file did not exist but I created it and made it executable ; nothing changed.  Here is a screenshot..

---

### Post by Zorael on 2010-01-26
And you do have **gtk2-engines-qtcurve** installed, I assume?

It's not immediately apparent (to me) what could be wrong. Try creating a new user and see if it affects him/her/it as well. If it does, then it's probably a package somewhere missing. But since you have the GTK+ Appearance module already, you'd really just need **gtk2-engines-qtcurve** to get QtCurve theming. (assuming the **.gtkrc-2.0-kde4** file is read)

The **gtk2-engines-qtcurve.rc.sh** script is part of **kubuntu-default-settings** and normally gets copied into your home directory upon user creation. If your user directory has been around since Hardy, perhaps it just predates that behavior.

Lastly, try changing something in the Font section of System Settings, and confirm that it's creating a **~/.fonts.conf** file for you. That won't fix font sizes (for which you need QtCurve), but it'll take care of keeping antialiasing and hinting settings consistent with your KDE apps.

---

