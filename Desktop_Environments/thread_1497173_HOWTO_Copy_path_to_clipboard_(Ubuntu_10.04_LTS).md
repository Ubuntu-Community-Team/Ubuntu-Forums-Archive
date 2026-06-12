---
title: "HOWTO Copy path to clipboard (Ubuntu 10.04 LTS)"
date: 2010-05-30
forum: Desktop Environments
---

### Post by paulbussmann on 2010-05-30
Here is a great post from David "coldrick":
 [http://ubuntuforums.org/showthread.php?t=104410](http://ubuntuforums.org/showthread.php?t=104410)
Unfortunately the post is read-only and can't be corrected to "Ubuntu 10.04 LTS" anymore.

Here is the original post. All I have altered is the script to be inserted.

Thanks to David "coldrick"! :-)

Have fun
Paul

---------------------------------------------------------
The modified post ( [http://ubuntuforums.org/showthread.php?t=104410](http://ubuntuforums.org/showthread.php?t=104410) ):


This is something I missed from Windoze: actually I think I always had to install it from somewhere.

Anyway, just install "xclip" from the Universe repository. Then create a script file - you could call it, say Copy Path to Clipboard, and copy/paste this into the file (note that the text starting with echo and ending with "clipboard" is all on one line):

#!/bin/bash
# old (Nov 2004): echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|/usr/X11R6/bin/xclip -selection "clipboard"
# new (May 2010):
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|xargs echo -n | /usr/bin/xclip -selection "primary"


Now save the file to ~/.gnome2/nautilus-scripts/ and make it executable.

Now you can right-click on a file or directory, choose Scripts->whatever you called the file, and its path will be in the clipboard.

I have gnome-clipboard-manager installed - dunno whether this is required to make this work.

Regards,
David

---

### Post by blchinezu on 2010-05-30
i don't know why would that be necesary.. you can just hit copy for the folder/file and than go and paste in a text editor or terminal

---

### Post by paulbussmann on 2010-06-04
Ooch! As easy. I did not even try to do it this way. Thank you very much, [blchinezu]("http://ubuntuforums.org/member.php?u=941322")!

---

### Post by Ophidion on 2010-11-17
> **blchinezu said:**
> i don't know why would that be necesary.. you can just hit copy for the folder/file and than go and paste in a text editor or terminal
Hahaha. I never thought this will exist! How did you know about it. I wasted 10 years out of my life copying the address from windows addressbar then copy the file name then paste it to the end of the path, what a pain. I found that nautilus has the ability to perform shell scripts, came here searching for one to copy the path. some written in python others in shell. It is very easy your way man. How can I reward you, I am new to the forum. Do they add points for users on thanking or so?...

---

