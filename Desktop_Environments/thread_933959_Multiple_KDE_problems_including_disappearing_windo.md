---
title: "Multiple KDE problems including disappearing window frames."
date: 2008-09-30
forum: Desktop Environments
---

### Post by Phyzzip on 2008-09-30
I'm running Kubuntu 8.04. Upon rebooting my computer I encountered the problems which I will detail below. As far as I know I've changed nothing that would affect KDE at all in months (yes I know everyone says this.) Off hand the only thing I can think of is that as this machine is almost never rebooted some update in the recent past clobbered a file that's read at start up.

First and foremost the window frame is missing. By that I mean basically all the widgets that KDE supplies to any application are missing. The title, bar, including the program name and the minimize, maximize and close buttons and the edges for screen resizing. The upshot of that is that I can't move or resize windows.

Secondly programs are not showing up in the bottom pane, when started the place holder entry with the hour glass appears but then disappears as soon as the program opens and is not replaced by the actual entry for the program. 

Also switching program focus is not working properly. Neither clicking on nor alt-tabbing is changing which window is on top although I can still interact with other windows underneath the last launched window if I can see them.

Finally among the symptoms I can see is that I have been reduced to a single desktop. When I go into the menu and attempt to add more nothing actually happens if I click ok or apply. (IE I increment the number of desktops I want, click apply, it grays out but I still only have one desktop).

Attached are a couple screen shots so you can see what I mean.

---

### Post by GeneralZod on 2008-09-30
Sounds like kwin is crashing, or failing to start - this would account for all of your symptoms, I think.  Open a terminal, and type

```

kwin

```

If any errors occur, please paste them here :)

---

### Post by Phyzzip on 2008-09-30
That's it.

Unfortantely it failed to start again on reboot so I suppose I should go looking for logs to see if it's starting at all.

---

