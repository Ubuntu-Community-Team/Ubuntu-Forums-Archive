---
title: "Gnome-terminal menu stuck in taskbar"
date: 2021-11-08
forum: Desktop Environments
---

### Post by The Cog on 2021-11-08
In gnome-terminal (and only gnome-terminal as far as I can tell), when I click a menu item it shows a one-line item in the taskbar instead of showing a proper modal drop-down menu. Often, the menu only has up and down arrows but no text between them.This makes selecting menu items very difficult. It seems to be attempting (badly) to emulate the way Apple put their drop-down menus at the top of the screen instead of on the appropriate window.
If I drag the window from the main screen to an external screen instead, the menus appear over the window as it should.

I don't know how it got like that, but I would very much like to restore its normal operation. I tried creating a new default profile, but that doesn't help. 
Any ideas, please? A config file I could try renaming or deleting somewhere, perhaps?

P.S. This is on Ubuntu 18.04.6 LTS

P.P.S. Gnome-tweaks has the same problem. It also has a warning triangle against the Shell theme selection, and that drop-down is disabled. I wonder if that is connected.

---

### Post by ActionParsnip on 2021-11-08
Have you tried a different theme?

---

### Post by The Cog on 2021-11-08
The only theme settings I can find are in gnome-tweaks. I've tried all 6 the themes offered there. They do affect the appearance of the menu items - the high contrast theme ensures that the text doesn't shrinks down to 0 pixels in height like most other themes do, but it's really ugly.
I notice that the menu items get spread horizontally across the taskbar, so a menu of more than 8-10 items will disappear off the right. And it does seem to be most applications that do this, of they are on the laptop screen rather than external monitor. I suspect the laptop may be effectively unusable without an external screen.
Do you know of a way of clearing your gnome settings back to default? I know other users on this software version don't have these problems.

---

### Post by ActionParsnip on 2021-11-08
Can you give a screenshot please, using your preferred theme.

---

### Post by The Cog on 2021-11-08
Aha! Found it. And it's a doozie!
In desperation, I renamed my home folder and made a new one (using a console login), just so I could lose all the personal settings. That was fine. About the first change I then made was to adjust the screen layout, putting the laptop screen below one of the two external screens (Settings, Devices, Screen Display). 
Bingo! That broke the menus on the laptop. 
With some experimentation, I can tell this is very specific to my setup: I have three screens: 1=(laptop, 1920x1080), 2=(Dell, 1920x1200), 3=(Dell, 1920x1080).
The two Dell screens are at the same height, with the laptop below (below either, no difference). If I put the larger screen on the left then everything is fine. 
If I put the smaller screen (3) on the left then all the menus on the laptop get displayed in the taskbar instead of in the application window, and sometimes the menu text is not visible, just up and down arrows.
I'll just swap the two monitors over. 

This is obviously just an edge case for Gnome, something most users are unlikely to see.
Thanks for trying to help, ActionParsnip. 
I'll mark the thread solved.

---

