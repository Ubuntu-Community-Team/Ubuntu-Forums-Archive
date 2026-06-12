---
title: "Gnome Color Chooser Problem"
date: 2010-05-18
forum: Desktop Environments
---

### Post by lynx1971 on 2010-05-18
Hi,

Have just set up a machine with Ubuntu 9.10 and then installed Gnome color chooser. Am using a dark background and wanted the Applications, Places and System icons in the panel to be white. GCC helped but it also changed the color of the text in the submenus (Recent Documents) to white. 

Besides the sub-menus, the menu bar text in Nautilus, Firefox and all other applications has also turned white. I've switched to a darker control but would appreciate if you could please specify where in GCC can I find the option to change the white color to black.

The attached pictures will give you an idea of the problem. Please help or else I will have to reinstall Ubuntu.


Thanks in advance,

Cheers

---

### Post by bra|10n on 2010-05-18
I'm not familiar with gnome color chooser but I think you will need to edit the theme gtkrc file for a fix. This can be a bit daunting at first, but an experience awaits you;)
I suggest that you copy the gtkrc file first so that at least you can revert to square one if need be.
And of course that will allow you to start all over again ;)

No need to reinstall because of this either, you would at worst delete the theme you are using and re-install that

---

### Post by lynx1971 on 2010-05-18
Thanks for your reply but GCC actually creates another file called .gtkrc-2.0-gnome-color-chooser which supersedes gtkrc and I've tried editing both but to no avail. [URL="http://ubuntuforums.org/member.php?u=1069087"]
[/URL]

---

### Post by bra|10n on 2010-05-18
> **lynx1971 said:**
> Thanks for your reply but GCC actually creates another file called .gtkrc-2.0-gnome-color-chooser which supersedes gtkrc and I've tried editing both but to no avail. [URL="http://ubuntuforums.org/member.php?u=1069087"]
[/URL]

Oh trust me it's in there.
I think you need to look for "workarounds" in the gtkrc file. Usually towards the bottom of the file.

---

### Post by lynx1971 on 2010-05-18
Thanks once again for your help. I re-edited the gtkrc and the GCC file and while I don't actually know what I did right, the color is now black as before.

---

### Post by bra|10n on 2010-05-19
> **lynx1971 said:**
> Thanks once again for your help. I re-edited the gtkrc and the GCC file and while I don't actually know what I did right, the color is now black as before.

Good to hear that colors are now readable. ;)
Well done, saved a re-install !!!
This might sound a little confusing but Ill give it a shot
Just be careful that you haven't altered text color to be "white" and then short-circuited the workaround... sort of like -1 x -2 = 2.
If you don't experience any problems elsewhere in the theme then you probably have stumbled on the right variable.
You can always prefix notes or previous settings in gtkrc with #, like [COLOR=Blue]# This setting is for foreground text ![/COLOR]
These won't affect the workings of the file and give you a reference to come back to later
cheers

---

### Post by lynx1971 on 2010-05-19
Hey I did not know that you could add text into the gtkrc file. Cool thanks this makes life simpler. I also just installed Compiz and wow the effects are like nothing you can find in Windows.

---

