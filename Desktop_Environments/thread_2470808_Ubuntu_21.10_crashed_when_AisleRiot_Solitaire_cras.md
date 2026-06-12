---
title: "Ubuntu 21.10 crashed when AisleRiot Solitaire crashed"
date: 2022-01-12
forum: Desktop Environments
---

### Post by erosman on 2022-01-12
While checking different games on **AisleRiot Solitaire**, it crashed. A popup showed that it crashed asking to send the report. However after clicking, the popup wouldn't go away and the game would continue or close. After few more clicks trying to close the game, Ubuntu crashed and froze (including mouse).

Nothing worked and I had to use hardware reboot.

I uninstalled **AisleRiot Solitaire **and reinstalled it from Ubuntu Software

However .....


[LIST]
[*]When trying after the reinstall, it started with the previously selected game
[*]Klondike does not come up among listed games
[/LIST]

Was **AisleRiot Solitaire **completely uninstalled?
Should I have done some cleaning after uninstalling? How?
How can I get a clean **AisleRiot Solitaire**?

---

### Post by VanillaMozilla on 2022-01-14
I can't help with the crashing, and I don't have Aisle Riot on this computer, so I can't check this.  But the user data for that program is probably in ~/.local/share/aisle or something like that.  (~ is your home directory.)  When the program is not running, you can delete that folder, and that should remove all the user data.  To be sure, start aisle riot and check the game statistics (it's in the menu).  The numbers should be at zero.  If you somehow got the wrong folder, you'd better quit aisle riot and restore the deleted folder.

---

### Post by erosman on 2022-01-15
Thank you.

When I searched the root after uninstalling **AisleRiot Solitaire**, I found out that there are still a lot of files left over.

The ones that was important were in *~/.config/gnome-games*

I removed 2 files (*aisleriot* & *aisleriot.accels*) and it seem to be reset.

It appears that **Klondike** is no longer listed anyway and replaced with **Canfield** as the default game.

---

