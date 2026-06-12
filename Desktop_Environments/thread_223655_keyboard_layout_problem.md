---
title: "keyboard layout problem"
date: 2006-07-26
forum: Desktop Environments
---

### Post by thec0der on 2006-07-26
Hello. When i try to add bulgarian layout every thing went ok, but when i try  to use another bulgarian keyboard layout i receive this error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Info about linux: Linux thec0der 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

xprop -root | grep XKB output:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us,bg", "phonetic,", "grp:alt_shift_toggle"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us,bg", "phonetic", "grp:alt_shift_toggle"

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd output:
 layouts = [us  phonetic]
 model =
 overrideSettings = true
 options = []

From this moment when i receive error, whatever i do with layouts i receive this error.
What to do now :confused: ? Is there any solution?

---

### Post by tjp.thomas on 2006-07-29
I have the same problem too... strange?!?

---

### Post by thec0der on 2006-08-01
Hello. How to fix this problem? I did not receive any answers.. :-(  Pls help bacause im fret.

---

### Post by cotcot on 2006-08-01
I have no solution.
It is a known issue in other distros too. There are a number of bug reports with solutions that work for some and does not work for others. Google with the first lines of the error report to see some maybe solutions.

---

### Post by tjp.thomas on 2006-08-01
I too have problems with this. I would suggest that someone prioritize finding a solution to this bug, since it will keep me from swicing to Ubuntu all together... and I suspect that others will have the same idea too. And I would really hate that!

---

### Post by thec0der on 2006-09-14
I read all related thread.. try every solution and nothing help. I see that a lot of ubuntu users have this problem, so suggest the admin of this forum to put some working solution as sticky thread.

---

### Post by wheezart on 2006-09-29
Hello people, i've found a workaround for this problem. It's a little low-tech but it worked for me. I had thesame problem on my girlfriends computer where any attempt to install a German layout resulted in the formerly mentioned error message.

What I did was the following:
I, ve made a drawer in one of the panels, just near the desktop switcher and made made three launchers in it:
Each of the loaunchers sets the keyboard layout to one of the three desired - US,DE,BG by using **setxkbmap** followed by he desired layout abbreviation *en,* *de,* *bg*. The codes can be easily derived from the country code and are usually a perfect match.

Wich means three launchers, (with different icons, mind you =) 
**setxkbmap** *en*
**setxkbmap** *de*
**setxkbmap** *bg*

Well that's it.

I guess global shortcuts can be made with metacity, to avoid the trip to the panel, until a solution for the bug is found.

~Cheers people!

---

