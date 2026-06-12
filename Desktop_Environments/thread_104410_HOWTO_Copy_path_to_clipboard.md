---
title: "HOWTO Copy path to clipboard"
date: 2005-12-16
forum: Desktop Environments
---

### Post by coldrick on 2005-12-16
This is something I missed from Windoze: actually I think I always had to install it from somewhere.

Anyway, just install "xclip" from the Universe repository. Then create a script file - you could call it, say Copy Path to Clipboard, and copy/paste this into the file (note that the text starting with echo and ending with "clipboard" is all on one line):

#!/bin/bash
# 
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|/usr/X11R6/bin/xclip -selection "clipboard"

Now save the file to ~/.gnome2/nautilus-scripts/ and make it executable.

Now you can right-click on a file or directory, choose Scripts->whatever you called the file, and its path will be in the clipboard.

I have gnome-clipboard-manager installed - dunno whether this is required to make this work.

Regards,
David

PS My very first HOWTO :-)

---

### Post by Nissa Leoni on 2007-06-02
Worked like a charm.  Thanks for posting this.

*Didn't need gnone-clipboard-manager, just xclip

---

