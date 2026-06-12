---
title: "Send copies to mail"
date: 2008-05-21
forum: Desktop Environments
---

### Post by ravica on 2008-05-21
Hi! I'm doing an important homework at my Ubuntu 7.04 (with Gnome) and I want know how I can send a copy of my work to my mail every time I want. Thanks.
I was trying the mail_file script of nautilus but it doesn't work and I think the easiest will be a script.:lolflag:

---

### Post by Youresorock on 2009-04-03
I figured out how to do this:

I wrote teh following script.  Modified from a nautilus script example to convert to jpeg.  Basically replaced everything in the while loop with what you (and I) wanted instead.

```

#!/bin/bash
# By: Youresorock

EMAIL=putyouremail@address.here

while [ $# -gt 0 ]; do
    7z a -mx=9 "/tmp/$1".7z "$1"
	/usr/bin/mutt -a "/tmp/$1".7z -s "$1: `date +"%Y.%m.%d"`" $EMAIL < /dev/null
    rm /tmp/"$1".7z
	shift
done

```

Step 1: max compression 7z the file/folder you give
Step 2: send via mutt (you must have mutt installed obviously)
Step 3: Profit!


You put this script in your ~/.gnome2/nautilus-scripts folder and set it executable.  (chmod +x filename)

I called mine "send2me"  You don't need the usual .sh for a shell script.

You just right-click the file/folder, and do "Scripts-->send2me" and it's sent.  Shows up in my gmail right away.  nice.  

:D  Linux rocks.

---

