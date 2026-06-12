---
title: "nautilus-open-terminal in unresponsive"
date: 2009-09-23
forum: Desktop Environments
---

### Post by r+9 on 2009-09-23
I've fallen in love with the "Open terminal here"
option so I've got

sudo aptitude install nautilus-open-terminal

in ever Ubuntu install I have at home, however, lately the 'button' has become unresponsive and does nothing when clicked

I've tried reinstalling but still nothing (even the lame windows-relog/reboot)

any idea what I broke?  Maybe some conflict with another package?

---

### Post by ben2talk on 2009-11-06
Sure, I lost this through the package 'nautilus-open-terminal' in synaptic, but it still works through a script included in the zip package - what's the name again? NScripts v3.6 on gnome.org or something similar - this one is included and works nicely. If you're not sure what to do, then select from #!/bin/bash down to dir"

right click desktop, or fire up text editor and paste it in. Save to the desktop as 'TerminalHere' or whatever.... no extension.

Fire up a Rootilus (gksu nautilus from the launcher ALT F2)and go to your /home/USER/Desktop and right click the file, make it executable - then cut it and move it to /home/USER/.gnome2/nautilus-scripts/

Now do ALT F2 'killall nautilus' and 'ALT F2 nautilus'

Right click, you'll see 'scripts>' and from there you can get to your script.

#!/bin/bash
#########################################################
#							#
# This are NScripts v3.6				#
#							#
# Licensed under the GNU GENERAL PUBLIC LICENSE 3	#
#							#
# Copyright 2007 - 2009 Christopher Bratusek		#
#							#
#########################################################

wdir=$(echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\\ /g')

gnome-terminal --working-directory="$wdir"

---

### Post by whysea on 2009-12-10
Well, I understand that we can cook up a new script, but why is nautilus-oen-terminal not working anymore. For me it has stopped today, after a recommended upgrade...

Very strange.

---

