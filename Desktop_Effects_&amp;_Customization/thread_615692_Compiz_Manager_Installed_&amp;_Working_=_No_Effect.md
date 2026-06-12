---
title: "Compiz Manager Installed &amp; Working = No Effects?"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by logonwheeler on 2007-11-17
I have an HP TC1100 Tablet PC with a Gefore4 Go 420 card with Gutsy installed. I was having some issues with the graphics driver so I decided that I would use Envy to get the correct ones installed. Done without any problems. Then I installed Compiz manager without any issues as well. I can go to the CCSM and check off and on any settings that I like.

However - none of the effects work with the defined keystrokes. When I go to System - Preferences - Apperance - Visual Effects it only allows me to select the "None - simple desktop" option even though I have "Normal" "Extra" and "Custom" to choose from.

If I try to select "Custom" I get the following message: "Desktop effects could not be enabled"

What am I doing wrong here?

---

### Post by lsutiger on 2007-11-18
How did you 'install' compiz?

---

### Post by Forlong on 2007-11-18
And post the output of ```
compiz
``` in a terminal.

---

### Post by logonwheeler on 2007-11-19
I determined that I needed to edit the /usr/bin/compiz file and commented out the line NVIDIA_MEMORY="65536" # 64MB and all was good. Turns out that even though the video card is 32 Mb and uses system RAM for extra, Compiz was not "allowed" to run on my card without this tweak.

Thanks to Phenest for the tip!

---

### Post by Forlong on 2007-11-19
Do _not_ edit /usr/bin/compiz!

Use ```
SKIP_CHECKS=yes compiz
``` instead.
If you create the file **~/.config/compiz/compiz-manager** and put that command in there, it will work without messing with system files.

---

