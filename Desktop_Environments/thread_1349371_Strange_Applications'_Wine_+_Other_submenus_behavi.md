---
title: "Strange Applications' Wine + Other submenus behaviour"
date: 2009-12-08
forum: Desktop Environments
---

### Post by laeg_ on 2009-12-08
Some months ago I incorrectly tried to upgrade/uninstall/reinstall WINE and ever since my Applications' *Wine* and *Other* submenus has just not been right.

Instead of the Wine submenu having neat little submenus for every Windows program I had installed, just like Program Files/All Programs, it now instead has 3 entries and everything has been put messily into the Other submenu, see below:

[IMG]http://i45.tinypic.com/v6rbzm.jpg[/IMG][IMG]http://i46.tinypic.com/314ffir.jpg[/IMG]

My last attempt at fixing it was yesterday. I removed WINE using synaptic and then through nautilus moved the .wine dir in ~ to trash and deleted it. Then leaving my /home partition intact I formatted my / partition before freshly installing Ubuntu 9.10 from disc.

On boot I reinstalled WINE only to find I still had the same problem and curiously enough even the messy Other menu whose symlinks lead to files which no longer exist. To test the Wine menu I quickly installed a small Windows program and it failed to give me a sub menu for it in Applications >> Wine >> as it should and did before.

Perhaps I need to first remove a file which governs the Applications menu from my /~ dir before reinstalling the system again?

Also, I don't remember having these windowsprogram.desktop and windowsprogram.ink files cluttering up my desktop before I initially had the problem so it may be related?

---

### Post by laeg_ on 2009-12-08
The below troubleshooting was recommended to me:

> Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers. In recent versions, a shortcut has been added to Wine's menu, along with a shortcut to winecfg.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

After following the above now all but 5 of the symlinks in *Applications >> Other* have been removed. Should I just remove them by right clicking the *Applications* menu and selecting *Edit* or is there a cleaner more complete way to do this?

[IMG]http://i50.tinypic.com/2n92sm.jpg[/IMG]

Also, as you can see this did not appear to remove any of the *.desktop* or *.ink* files from my desktop, again should I just move them to trash or is there a cleaner more complete way to do this?

Lastly, I'm anxious to see if installing Windows programs will once again give me nice submenus within the *Applications >> Wine* submenu like it used to but I don't want to reinstall WINE yet until the remaining symlinks and redundant files on the desktop are completely removed.

---

