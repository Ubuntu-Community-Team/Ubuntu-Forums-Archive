---
title: "rotate desktop doesn't work"
date: 2006-03-22
forum: Desktop Environments
---

### Post by pesachzon on 2006-03-22
Hi, i have a rotating lcd monitor and i'm trying to rotate the desktop to match.
The rotation controls in the kde control panel -> display are greyed out.

Here's the error message i get form xrandr:

Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Anyone knows how to fix it?

---

### Post by daller on 2007-06-27
Quite a while...

Have you got a fix?

Does the xrandr work?

DESCRIPTION
       Xrandr  is  used  to set the screen size, orientation and/or reflection.  The -s option is a small integer index used to specify which size the screen should be set to.
       To find out what sizes are available, use the -q option, which reports the sizes available, the current rotation, and  the  possible  rotations  and  reflections.   The
       default size is the first size specified in the list.  The -o option is used to specify the orientation of the screen, and can be one of "normal inverted left right 0 1
       2 3".

What about this:

sudo xrandr -o left

???

---

### Post by john3333 on 2007-06-28
Try the suggestions in this link: [http://ubuntuforums.org/showthread.php?t=478244&highlight=rotation+dell](http://ubuntuforums.org/showthread.php?t=478244&highlight=rotation+dell)

---

