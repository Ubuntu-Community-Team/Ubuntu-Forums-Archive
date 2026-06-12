---
title: "Launch settings directly from Whisker menu"
date: 2014-04-22
forum: Desktop Environments
---

### Post by otoh on 2014-04-22
Using Xubuntu 14.04 here - Whisker menu works well, but ideally I'd like to be able to launch settings directly via keyboard. Eg if I want to look at my printers, rather than:
[LIST]
[*]WhiskerMenu > 'settings' > then click Printers
I'd like to:
[*]WhiskerMenu > 'printers'
[/LIST]

I sort of achieved this by using the Menu editor and removing Settings:Settings from the Printers application. But when I tried it with the Desktop settings, it worked as expected on Whisker menu, but removed it from the settings dialog.

So in short, I'm missing the logic that:
[LIST]
[*]Whisker menu uses to determine which items to show/hide;
[*]The System settings dialog uses to determine which items to include in itself.
[/LIST]

Any ideas?

---

### Post by Jordan_Cameron on 2014-04-22
Have you tried just searching for "Printers"?  If I recall correctly, whiskers menu has a search feature, and xfce settings are "module" like things, instead of all being embedded into an app.  So if you search for printers, does it come up?

---

### Post by lucast on 2014-04-23
I have a similar issue.  I would like to display things like the 'System Updater' in the Whisker Menu, under system.  But when I edit the menu using the MenuLibre and change the categories I can either have it displaying in the Whisker Menu or System Settings, but not both.

I guess I could create a second entry for each item I want but that seems a little stupid.

---

### Post by otoh on 2014-04-23
> **Jordan_Cameron said:**
> Have you tried just searching for "Printers"? If I recall correctly, whiskers menu has a search feature, and xfce settings are "module" like things, instead of all being embedded into an app. So if you search for printers, does it come up?

Yes - by default, Printers does not show up in the menu - as you say, it is an app so should get found but Whisker menu seems to specifically exclude items that appear in the settings dialog - requiring you to go via settings to get to it.

---

### Post by otoh on 2014-04-23
> **lucast said:**
> I have a similar issue.  I would like to display things like the 'System Updater' in the Whisker Menu, under system.  But when I edit the menu using the MenuLibre and change the categories I can either have it displaying in the Whisker Menu or System Settings, but not both.

I guess I could create a second entry for each item I want but that seems a little stupid.

Aha, so it's not just me! I tried to figure it out but I still can't. I had success with Printers - removed Settings:Settings and it shows in both contexts. Then I tried another, Passwords - I installed seahorse and it goes into settings but not into WM. Then I mucked about with the .desktop files in ~/.local/share/applications - I made seahorse.desktop exactly the same as system-config-printer.desktop (apart from name/executable/comment)... and it then shows in WM but not in Settings.

Like you, not sure I can be bothered to create duplicates... but do let me know if you figure it out :)

---

### Post by Dennis N on 2014-04-23
> So in short, I'm missing the logic that:

Whisker menu uses to determine which items to show/hide;
The System settings dialog uses to determine which items to include in itself.
    
As I understand it, the System Settings window is part of the same single menu structure (like a separate category) except it is configured to display in a separate window. An item can only appear once in the entire menu (including the settings window).

The menu conforms to these rules:
[http://standards.freedesktop.org/menu-spec/menu-spec-latest.html](http://standards.freedesktop.org/menu-spec/menu-spec-latest.html)

---

