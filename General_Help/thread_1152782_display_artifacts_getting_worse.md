---
title: "display artifacts getting worse"
date: 2009-05-08
forum: General Help
---

### Post by francesco44 on 2009-05-08
hello folks

I upgrade to jaunty for two thinkpad X31 and 1 X30

Everything is fine with the X31.....but I have serious display problem with the X30

First with ALL the word processor or editor including This One.from time to time when typing a line.....the entire line vanish.....(in a blak line), usualy after one or two stroke the line shows again.

Second titles in different windows are transformed with "bad" fonts that is sequences of letters shows as white rectangles or are covered with horizontal gray lines...All this happens indepsndently of the themes

At last, the whole screen is progressively invaded with left alphabetic characters, horizontal lines etc....the small images (for ex the smilies turn to grey square)

I think this is undoubtful related to a driver for Intel display devices as the X30 has one and X31 rely on ATI

Any Suggestion?

Thanks to all

Thanks to all

---

### Post by Peter09 on 2009-05-08
I am having display corruption problems on a laptop with an Intel Chip as well, not seen any fix for it as yet.

---

### Post by francesco44 on 2009-05-08
With the more correct label "display corruption" it shows that it is a registered bug

look at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/)

You will notice that the 4th or 5 comment is related to a thinkpad X30 which shows....exactly the symptoms I observed.


I will now look for any solution

---

### Post by francesco44 on 2009-05-08
After reading the section "known Jaunty bugs" at the beginning of this section and the bug report.....it appears.....on a firs analysis that three solution might be used

in any case edit the following file :

sudo gedit /etc/X11/xorg.conf


After that you may add to your device section the two following lines:

#	Option "AccelMethod" "UXA"
#	Option "MigrationHeuristic" "greedy" 

The first one if you activate it gives a real acceleration but is unstable....it works one time upon three!

The second one is more secure and seems to be working well on an X30 anyway

so presently my device section is the following one:

Section "Device"
	Identifier	"Configured Video Device"
#	Option "AccelMethod" "UXA"
	Option "MigrationHeuristic" "greedy" 
EndSection

See you all to the next bug (if this happens!):guitar:

---

