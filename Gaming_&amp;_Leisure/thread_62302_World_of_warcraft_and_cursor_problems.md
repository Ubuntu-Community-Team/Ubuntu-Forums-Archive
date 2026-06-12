---
title: "World of warcraft and cursor problems"
date: 2005-09-04
forum: Gaming &amp; Leisure
---

### Post by ianpeters on 2005-09-04
I'm using the latest WoW patch and everything and from Windows XP, everything works perfectly. But of course I don't want to dual boot, so I installed Cedega 4.4 to give WoW a try on Ubuntu.

It loads without a hitch and all but as soon as I try to click something, NPCs, mailbox etc., nothing happens. Although I can click on spells, backpack and so on, but nothing that can be interacted with reacts to a mouse-click.

Anyone know a solution to this?
Thanks in advance!

---

### Post by Perfect Storm on 2005-09-04
> Two work arounds have been discovered for the mouse selecting issue that has occurred since the World of WarCraft 1.5.1 patch.

1) This workaround may not work on all distros, may prevent other games (such as Half-Life 2) from running but should not cause a speed decrease.
open a console/terminal window and run
export WINEPRELOADER_SETVALEGACY="no"
then launch Cedega or Point2Play from the same terminal window.
This would need to be set each time you open a new terminal window to play the game.

2) This workaround should work for all users on all distros but may cause a frame rate drop.
Edit the World of WarCraft configuration file with your favorite text editor:
command line users: /home/USERNAME/.transgaming/config
Point2Play users: /home/USERNAME/.point2play/configuration_profiles/NAME_OF_WOW_CONFIG
Add the following section to the config file:
[AppDefaults\\wow.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
This change will remain persistent as long as you continue to use that configuration file for World of WarCraft. This change may need to be removed for future versions of Cedega.

Taken from Transgaming forum. [http://transgaming.org/forum/viewtopic.php?t=3149](http://transgaming.org/forum/viewtopic.php?t=3149)

---

### Post by ianpeters on 2005-09-04
Thanks for your help, for some reason that post didn't turn up in my forum search. This solution worked: 

1) This workaround may not work on all distros, may prevent other games (such as Half-Life 2) from running but should not cause a speed decrease.
open a console/terminal window and run
export WINEPRELOADER_SETVALEGACY="no"
then launch Cedega or Point2Play from the same terminal window.
This would need to be set each time you open a new terminal window to play the game. 

Now to just get better FPS  :)

---

