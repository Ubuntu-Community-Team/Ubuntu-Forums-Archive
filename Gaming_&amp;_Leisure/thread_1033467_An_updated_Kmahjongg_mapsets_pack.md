---
title: "An updated Kmahjongg mapsets pack"
date: 2009-01-07
forum: Gaming &amp; Leisure
---

### Post by qyot27 on 2009-01-07
I had noticed, when trying to find additional mapsets for Gnome Mahjongg and Kmahjongg, that there wasn't a lot of development out there.  The one resource was on the old KDE Games page, where there was a pack of 60 or 70 some mapsets.  However, as I have KDE4 installed, said mapsets didn't want to play nice with the version of Kmahjongg that comes with it.

So, as I couldn't find any reference to anyone trying to update these mapsets, couldn't find an already-updated set of them, and quite frankly didn't want to wait in the hopes that either the main dev team or somebody else would do it eventually, I took it upon myself to update them.  It wasn't hard at all to bring these up to a level that the current version of Kmahjongg can use, it was only rather tedious.

Just unpack, stick the layouts in /usr/share/kde4/apps/kmahjongg/layouts, and have at it.

The ones included are the same as the one from the old main KDE Kmahjongg site.  These sets work perfectly, and caused no problems for me:
Four Winds, Alien, Altar, Arena, Arrow, Atlantis, Aztec, Balance, Bat, Bug, Castle, Chains, Checkered, Chip, Clubs, Columns, Cross, Dragon, Eagle, Enterprise, Explosion, Flowers, Future, Galaxy, Garden, Girl, Glade, Grid, Helios, Hole, Inner Circle, Key, KM, Labyrinth, Mask, Maya, Maze, Mesh, Moth, Order, Pattern, Penta, Pillars, Pirates, Rocket, Shield, Spider, Squares, Squaring, Stadion, Stairs, Star, Star_ship, Swirl, Teatre, Temple, The Door, Time Tunnel, Tomb, Totem, Up & Down, Well, X-shaped

The following four were troublesome, causing Kmahjongg to crash with a SIGABRT error when trying to select them from the list or (if more than one of them was in the directory at the same time), crashing with SIGABRT just by trying to go into the Configure Kmahjongg area.  I've included them in the 'trouble' folder so that anyone who wants to see if they can fix the issue can take a swing at them, but they aren't mixed in with the others for convenience:
Butterfly, Eye, Vi, Volcano


NOTES:
I have no idea if this will work the same on Kubuntu (or even other non-Ubuntu distros, for that matter), as the desktop file that's paired with each layout has a line that says 'X-Ubuntu-Gettext-Domain=desktop_kdegames'.  I have an Ubuntu 8.10 setup under which I simply have KDE installed next to Gnome.  I don't know if that line needs to be adjusted for use in Kubuntu nor do I know if the desktop file in general is absolutely necessary for use with Kmahjongg (I made them simply for the fact that they exist with the mapsets that are installed by default, but I don't know if that's something unique to the Ubuntu builds or if it's required by the program itself).

Also, the desktop files only have language-specific references for en_US, as I don't know the other name references and whatnot (and didn't want to leave the existing ones in there because it would surely screw up the choice dialog for non-English setups).  So these may or may not integrate as nicely into other locales, although I can assume from the regular Name= line that there won't be a problem getting them to load.  At least this is a start to getting these completely up to speed.

---

