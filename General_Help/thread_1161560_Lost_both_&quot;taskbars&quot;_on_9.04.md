---
title: "Lost both &quot;taskbars&quot; on 9.04"
date: 2009-05-16
forum: General Help
---

### Post by Forgoten Dynasty on 2009-05-16
Ok so i was using ubuntu fine. Rebooted loaded windows was playing around with windows then when i switched back to ubuntu both my taskbars are gone.

I can open terminal with alt f2 but none of the commands I found in other threads where for 9.04 and didn't work. Does anybody have any suggestions on what i should do?

---

### Post by mb_webguy on 2009-05-17
To reset your Gnome panels to the Ubuntu defaults...
[LIST=1]
[*]In the terminal or run dialog (Alt+F2), enter the command "rm -r ~/.gconf/apps/panel" or "mv ~/.gconf/apps/panel /path/to/somewhere/else" if you'd rather back up your current settings than delete them.
[*]Log out, then back in.
[*]There is no step 3.
[/LIST]

---

### Post by Forgoten Dynasty on 2009-05-17
OS i booted in to the recovery mode and restored the graphical stuff. And they came back but then my beryl would not work. I would have the manager open and everything would look good. I tried to uninstall it and it would go threw but it would still be in the applications list. I could open the manager so that the ruby would be in the tray but then nothing and the right click menu would work but I couldn't open any thing that had to do with it.

After all that I turned my computer off for the night and when i turned it back on poof they are gone again.

EDIT: also that command didn't work



EDIT 2: ive concluded it must be my video card drivers. I fixed graphical issues again then I went back in and went to hardware drivers and enabled the suggested video card drivers for my video card (Nvidia gforce 5500) and when i restarted for the effect to show I once again lost my bars

---

### Post by cwbar_1 on 2009-05-17
Not sure if this will help but,,,, try creating a new user. Log out and and then log back in as the new user.  If you have the taskbars in the new user set-up, post back.

---

### Post by Reilithion on 2009-05-18
This issue is not unique.  I believe several gnome-related bugs have been introduced in Jaunty.  Among them, this.  Perhaps it can be fixed by changing configuration or troubleshooting, or perhaps it will require changes to Gnome code.  Only a Gnome guru could tell us.  And I am not one.

See also this thread:  [http://ubuntuforums.org/showthread.php?t=1162847](http://ubuntuforums.org/showthread.php?t=1162847)

---

### Post by Forgoten Dynasty on 2009-05-21
It was something to do with beryl.

If i have beryl set to boot on start then i loose both task bars.

If not everything is fine and i can open beryl later and have ti work

---

