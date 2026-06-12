---
title: "Beryl Makes Desktop go black"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by mikeybthepilot on 2007-07-08
I've been searching for the answer to this everywhere and haven't found it yet.

I recently installed Feisty Fawn (32bit) on an AM2, 1 GB Ram, with an nVidia 6150 card.  I previously had Beryl working on Dapper working with the 6150 card and an Athalon XP chip and it was great but now I can't seem to figure out what's going on here.

I installed the newest nVidia drivers and Beryl but when I run beryl-manager the desktop turns black although I still have the taskbars, also firefox disappears completely and any open windows loose their titlebars although I can still see them.  The beryl effects seem to work as the info bubbles and whatnot do their thing.  I can also rotate the cube but there is no skydome.  Any ideas on how to fix this??  I've tried 'force aiglx' and the problems stay the same but the computer gets a lot slower.  I've also tried 'force xgl' but that froze the computer something fierce!  Any help would be much appreciated!

I'm pretty sure this problem hasn't been posted yet but I could be wrong...

---

### Post by ajmorris on 2007-07-08
> **mikeybthepilot said:**
> I've been searching for the answer to this everywhere and haven't found it yet.

I recently installed Feisty Fawn (32bit) on an AM2, 1 GB Ram, with an nVidia 6150 card.  I previously had Beryl working on Dapper working with the 6150 card and an Athalon XP chip and it was great but now I can't seem to figure out what's going on here.

I installed the newest nVidia drivers and Beryl but when I run beryl-manager the desktop turns black although I still have the taskbars, also firefox disappears completely and any open windows loose their titlebars although I can still see them.  The beryl effects seem to work as the info bubbles and whatnot do their thing.  I can also rotate the cube but there is no skydome.  Any ideas on how to fix this??  I've tried 'force aiglx' and the problems stay the same but the computer gets a lot slower.  I've also tried 'force xgl' but that froze the computer something fierce!  Any help would be much appreciated!

I'm pretty sure this problem hasn't been posted yet but I could be wrong...

i dont know if it has been posted on these forums.... but that is a well known nvidia bug :(  there are ways to fix it though :)

press ALT+F2 and type in : ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

then restart X (ctrl+Alt+backspace)
and hopefully it works.... if it does not, dont worry, there is more tweaking we can do to your xorg.conf file that will fix it :)

---

### Post by fycloops on 2007-07-08
I can't remember where I saw it but someone posted about adding the lines:

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

to my xorg.conf in the "device" section. This helped fix my non-existant titlebars...

To edit the file:

sudo gedit /etc/X11/xorg.conf

Hope this helps.

Fyc

---

### Post by ajmorris on 2007-07-08
also i just did a search and found this thread : [http://ubuntuforums.org/showthread.php?t=493511](http://ubuntuforums.org/showthread.php?t=493511)

some more stuff to try :)

---

