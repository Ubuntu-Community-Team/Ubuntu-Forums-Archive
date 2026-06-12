---
title: "WINE Tip, virtual explorer window"
date: 2011-12-30
forum: Gaming &amp; Leisure
---

### Post by r+9 on 2011-12-30
I run this little bash script to help me 

# this first bit gets the screen resolution for you
# 
Screen=`xrandr | grep \* | awk '{print $1}' | head -1`
wine explorer /desktop=a_dekstop_name,$Screen <path to .exe> &


this will open a nice blue screen and plop your wine game into it.  It allows you to tab over to other desktops without all the wonky behavior.

I'm sure this is a repeat of other posts but I wanted to add my two bits.

---

### Post by thatguruguy on 2011-12-30
**UBUNTU FORUMS Tip, placement of threads**

Put threads related to Wine in the Wine sub-forum.

You can find it [here]("http://ubuntuforums.org/forumdisplay.php?f=313").

I'm sure this is a repeat of other posts but I wanted to add my two bits.

---

