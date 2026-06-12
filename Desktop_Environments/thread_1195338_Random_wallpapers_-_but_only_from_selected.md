---
title: "Random wallpapers - but only from selected"
date: 2009-06-23
forum: Desktop Environments
---

### Post by gemme on 2009-06-23
I've built a great collection of backgrounds in a [_Change Desktop Background_]("https://help.ubuntu.com/community/UbuntuEyeCandy?action=AttachFile&do=view&target=Screenshot-Appearance+Preferences.png") window (Theme preferences).

Is there any way to set a new one (from those) at every login?

I know there are many applications and scripts that can do that if the files would be **from one directory, but they aren't** :(

Does any way exists that would get the list from that window I built my collection in and cycle through it?

---

### Post by Paul Miller on 2009-06-23
You want to install drapes.
[php]
sudo apt-get install drapes
[/php]
Then start it up with
[php]
drapes &
[/php]
from the terminal or just use 'drapes' from the run dialog.  It'll show an icon in the system tray. 

**Configuring:**

Make sure that "Shuffle periodically" is unchecked if that's not what you want.  Right click on the icon and choose Preferences -> General.  Make sure "Start Desktop Drapes on start" and "Switch on start" are selected.  Voila.  This should do exactly what you want.

---

### Post by gemme on 2009-06-23
> **Paul Miller said:**
> You want to install drapes.

Paul, I've already tried drapes, but it has its' own list of wallpapers. I couldn't drag anything from my collection to drapes.

---

### Post by cariboo on 2009-06-24
I use wallpaper-tray, it is very configurable and it is available in the repositories.

See screenshot.

---

### Post by gemme on 2009-06-25
cariboo, it's the same as Drapes - it has it's own list and no way of importing existing collection.

Or... is there any way to automatically get files listed in [FONT="Courier New"]**~/.gnome2/backgrounds.xml**[/FONT] (that's the list I'm talking about) and put it there?

---

### Post by gemme on 2009-06-28
It seems I was wrong - I deleted old Drapes config file and it nicely picked the collection.

However, all items had a setting which indicated how to place it on a desktop:
scale / place in the middle of the screen etc.

(I'm sure you have some wallpapers that look great only when shown in a specified way :) )

Drapes seems to [have only a global setting]("https://bugs.launchpad.net/drapes/+bug/231469") for all images. Anyone has a trick for this?

---

### Post by gemme on 2009-10-04
If anyone's interested, I have created a python script that changes the wallpaper to a random one and sets the display correctly.

```
#!/usr/bin/python

# Change Gnome wallpaper to a random one
# (c) 2009 M. Barucha
# Licenced under GNU General Public License v2.0
# Enjoy!

import os
from xml.dom import minidom
import random
import gconf

tla = minidom.parse(os.path.expanduser('~')+'/.gnome2/backgrounds.xml')

choices = [e for e in tla.documentElement.childNodes
	if e.nodeType == e.ELEMENT_NODE and e.getAttribute('deleted') == 'false']
chosen = random.choice(choices)

client = gconf.client_get_default()

client.set_string('/desktop/gnome/background/picture_filename',
	unicode(chosen.getElementsByTagName('filename')[0].firstChild.nodeValue).encode("utf-8"))
client.set_string('/desktop/gnome/background/picture_options',
	chosen.getElementsByTagName('options')[0].firstChild.nodeValue)
client.set_string('/desktop/gnome/background/color_shading_type',
	chosen.getElementsByTagName('shade_type')[0].firstChild.nodeValue)
client.set_string('/desktop/gnome/background/primary_color',
	chosen.getElementsByTagName('pcolor')[0].firstChild.nodeValue)
client.set_string('/desktop/gnome/background/secondary_color',
	chosen.getElementsByTagName('scolor')[0].firstChild.nodeValue)

```

---

### Post by Arthur_D on 2009-10-04
Nice! I've found that the applications I've tried for this either is unstable or doesn't exclude the built-in wallpapers.
Of course, I would love to use an application that auto-starts each time I log in for this, but a script is better than nothing. ;)

Thank you. :)

---

### Post by gemme on 2009-10-05
It took me a lot of time, but to succesfully run in crontab it needs to be run as this:

```
0 * * * * DISPLAY=:0.0 /usr/bin/sudo -H -u user "/full/path/mati-random-background.py"
```

Hope it'll save somebody some time.

---

