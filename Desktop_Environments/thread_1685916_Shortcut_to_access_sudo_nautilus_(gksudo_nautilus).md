---
title: "Shortcut to access sudo nautilus (gksudo nautilus) from the current window."
date: 2011-02-11
forum: Desktop Environments
---

### Post by wjz on 2011-02-11
Hi this is my first post. Is it possible to change my current nautilus window to have sudo capabilities,? e.g. to delete locked files. It may be lazy but if it takes a lot of navigation then it would be handy to somehow activate sudo from the open window without the terminal command (gksudo nautilus)  which always begins at root.

 Thanks in advance.

---

### Post by Copper Bezel on 2011-02-11
You can set up a Nautilus script for it, yes. I use this one by Nguyen Duc Long:

> #!/bin/bash
#
# this code will determine exactly the path and the type of object,
# then it will decide use gedit or nautilus to open it by ROOT permission
#
#
# Nov 19, 2010
#Copyright by Nguyen Duc Long <Email: [email]longnd.s8@gmail.com[/email]>
####################################################################################

# Determine the path
if [ -e -n $1 ]; then
	obj="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
else
	base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
	obj="$base/${1##*/}"
fi
# Determine the type and run as ROOT
if [ -f "$obj" ]; then
	gksu gedit "$obj"
elif [ -d "$obj" ]; then
	gksu nautilus "$obj"
fi

exit 0

Copy this text into a new text document named "Open as Root" and set it as executable by right-clicking it and selecting the "Permissions" tab, then checking the checkbox for "Allow executing". Now, open Nautilus and right click anywhere in the content pane. In the right-click menu, select Scripts - > Open Scripts Folder. Move the text document you created here. Now, to open a folder as root, right-click it, select Scripts, then "Open as Root".

What's cool about this script is that it works for text config files, too. They'll open in a root GEdit session.

---

### Post by ubername on 2011-02-11
Install the package nautilus-gksu

This allows you to open folders / files as root. (Wtihin normal nautilus, right click on folder/file and select 'open as administrator')

---

### Post by Copper Bezel on 2011-02-11
My tip came with a bonus feature. = P

---

### Post by wjz on 2011-02-11
Hi lads, I went with Mr Bezels somewhat more work intensive approach and got it working thanks a million. Tried nautilus-gksu as well and after restarting nautilus (nautilus -q and then nautilus) it worked a treat.

Thanks again.

---

### Post by zkneebone on 2011-04-19
Also, you can put a link to the script on your top panel, that makes it into a drop target. To do that, just right click the panel and "Add to Panel..." then find your script and name it something. Just drop a file or folder on the panel icon from nautilus to open it in gksudo.

---

### Post by Alchera on 2012-10-17
> **ubername said:**
> Install the package nautilus-gksu

This allows you to open folders / files as root. (Wtihin normal nautilus, right click on folder/file and select 'open as administrator')
Add Open As Administrator to the Context Menu in Ubuntu 12.04 (Precise Pangolin)

[http://www.liberiangeek.net/2012/04/add-open-as-administrator-to-the-context-menu-in-ubuntu-12-04-precise-pangolin/?ModPagespeed=noscript](http://www.liberiangeek.net/2012/04/add-open-as-administrator-to-the-context-menu-in-ubuntu-12-04-precise-pangolin/?ModPagespeed=noscript)

:biggrin:

---

### Post by nothingspecial on 2012-10-17
[IMG]http://imageshack.us/a/img69/5481/suddenlyamuffin.jpg[/IMG]

---

