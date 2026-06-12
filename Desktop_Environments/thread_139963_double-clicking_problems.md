---
title: "double-clicking problems"
date: 2006-03-05
forum: Desktop Environments
---

### Post by racter on 2006-03-05
Hi - i just switched to kubuntu 5.10.  i love it!

however, i cannot seem to double-click on things.  fortunately the default setting is "single-click to open files," so i am still able to easily open files in konqueror.  but when i double click on a word in a text file, nothing happens (usually that would select the word).  also when i get a file browsing dialog (like in firefox) i have to choose the folder with a click and then click 'OK' or press 'enter' in order to activate it.

i tried raising the double-click interval in system settings way up as far as 2000ms but that didn't help.  this is on a laptop with a touchpad, but the problem is still there when i'm using a usb mouse.

is there a xorg.conf setting or something for double-click?

thanks

---

### Post by racter on 2006-03-05
ok actually i can double-click in konsole + kate, but not in firefox, jedit, xmms or anything that doesn't start with a 'K' it seems.  weird.

==

actually, this ended up being a side effect of the 'double clock speed' issue - [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

i'm guessing that it only showed up in non-k apps because the generous double-click time i set in kde's configuration was concealing the problem from me in k apps.  (the clock was probably running to fast to catch my double-clicks...?).

another interesting symptom of this 'double clock speed' issue is that animations (including animated .gifs in firefox) were all running at 2X.

---

