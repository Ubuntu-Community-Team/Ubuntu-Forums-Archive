---
title: "ZSNES problems"
date: 2020-07-01
forum: Emulators
---

### Post by snesbmg on 2020-07-01
I can't open zsnes as I set the resolution too high. When I open zsnes in terminal it says: 

Starting Mouse detection.Unable to poll /dev/input/event15. Make sure you have read permissions to it.
Unable to poll /dev/input/event14. Make sure you have read permissions to it.
Unable to poll /dev/input/event13. Make sure you have read permissions to it.
Unable to poll /dev/input/event12. Make sure you have read permissions to it.
Unable to poll /dev/input/event11. Make sure you have read permissions to it.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Could not set 1600x1200-GL video mode.

How do I open Zsnes now?

---

### Post by Holger_Gehrke on 2020-07-26
To get access to the /dev/input/event* devices (to get rid of the 'unable to poll ...' messages) you have to be a member of the group 'input'. You can probably do that from some graphical applet for changing user accounts or you can use usermod from the command line 'usermod -aG input [I]username'.

[/I]ZSNES has a configuration file in '~/.zsnes/zsnesl.cfg'. Open that file with any editor, it's human readable and quite well commented. The setting you want to change is 'cvidmode='. It' probable set to '19' now (at least that's what the comments in the file say would be the value for 1600x1200). Try '15' (which should be 1024x768 in a window).

Alternatively you can call zsnes with the '-v num' option with num being the number of a video mode. So 'zsnes -v 15' should give you zsnes running in a window of 1024x768 pixels.

Holger

---

