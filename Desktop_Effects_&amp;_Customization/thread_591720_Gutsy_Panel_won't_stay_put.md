---
title: "Gutsy Panel won't stay put"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by FearNoIdea on 2007-10-25
Reformatted the partition and did a clean install of 7.10  Love it.  I've been tweaking with my interface for the last hour or so.  I've loaded awn, removed the bottom panel and set my top panel to NOT expand, and TO autohide.  So far so good.  When I log out and log back in, my top panel is on the bottom.  Any thoughts?

---

### Post by FearNoIdea on 2007-10-25
Update:  The panel was not allowing me to move it to a new location.  Ie... Put my top panel back on the top.  For some reason if I check "expand" in the properties it allows me select a different location for the panel.  Once repositioned I can disable "expand" again.  Another thing... All of my panel objects are rearranged every time I log in...

---

### Post by DaymItzJack on 2007-10-25
Make all your panels how you want them, then go into the Session manager and tell it to save the current session and that fixed some other problem for me.

---

### Post by cometdog on 2007-10-27
Same exact thing is happening to me.

When uncheck the "expand" box in the properties for the top panel, everything is fine.  When I log out and log back in, it's back at the bottom and slightly scrambled (menus on the right, time on the left, shut down button in the middle).

When I leave the panel unexpanded, it won't allow me to reposition it via the dropdown box in properties.  However, I am able to drag it back to the top.  We'll see if it stays there now, or if the save session tip works.

I just installed Avant Window Navigator, and I wasn't sure if that was somehow contributing to this problem.  I see the OP didn't mention it, though, so perhaps it's completely unrelated.

---

### Post by cometdog on 2007-10-27
OK, will continue relating bizarre sequence of events.

After dragging the panel back to the top (and posting the above message), I logged out and back in again.  This time the panel remained at the top, but my desktop background had disappeared and was just black.  The buttons on the panel were still scrambled, because I hadn't wanted to reorganize them multiple times during troubleshooting.

I noticed that nothing happened when I right-clicked on the desktop.

I opened System->Preferences->Appearance, and the background re-appeared as Appearance was opening.  I closed Appearance, but I was still unable to right-click on the desktop.

I opened Appearance again, and looked at the Visual Effects tab.  The "Normal" radio button was selected instead of the "Custom" one.  I selected "None" to turn off Compiz Fusion, and exited Appearance.  Still no luck with the right clicking on the desktop.  I re-opened Appearance and selected  "Custom" again, closed Appearance, expanded the top panel, and logged out.

This time upon logging in, my buttons were mysteriously back in the correct order in the top panel.  Desktop background still black and no right-clicking.


That's my current situation.

I'm really not sure where to start with troubleshooting.  I could try to uninstall AWN, I could try to remove some kind of preferences file in my home directory, not sure what else.  Anyone have suggestions?

---

### Post by FearNoIdea on 2007-10-29
I tried saving my session.  The same thing happens when I log out and log back in.  The top unexpanded panel is again at the bottom of the screen, with the icons scrambled.  The other strange thing is that my login screen keeps changing.

---

### Post by mikespug on 2008-01-21
I don't know if you're still looking for a solution but here is what worked for me...

> Alt-F2 Run gconf-editor
> apps-panel-toplevels-panel_0
> change "y_bottom" integer to 1 instead of -1

To quote from the settings "Long description"

"The location of the panel along the y-axis, starting from the bottom of the screen. If set to -1, the value is ignored and the value of the y key is used. If the value is greater than 0, then the value of the y key is ignored. This key is only relevant in un-expanded mode. In expanded mode this key is ignored and the panel is placed at the screen edge specified by the orientation key." 

Essentially what is happening is y_bottom, when set to -1, is looking for a y value that relates to your monitors y axis that hasn't been set in the panels settings.  Changing the value to 1 tells the panel to ignore the y value.

Worked for me anyway.  Hope it helps!

---

