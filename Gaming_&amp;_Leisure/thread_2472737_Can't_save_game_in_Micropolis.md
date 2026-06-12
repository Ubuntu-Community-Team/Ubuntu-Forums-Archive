---
title: "Can't save game in Micropolis"
date: 2022-03-10
forum: Gaming &amp; Leisure
---

### Post by Objekt on 2022-03-10
Installed Micropolis the usual way (via Snap).  Game runs fine, but I can't save a game in any way.

The default save location (/snap/micropolis/153/usr/local/share/micropolis) cannot be saved in; I get a "read-only filesystem" error in the game's dialog (where it shows messages about various stuff).

Fine, so I try to save in my /home/username folder.  In that case I get "Permission denied."

I found a couple of old threads complaining about this problem, but no solution.

What's the fix?  I cannot save my game anywhere.

---

### Post by DuckHook on 2022-03-10
You will need to change the settings for the snap version. Instructions here: [https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)

Although it is mislabelled, you will need to enable "Read/Write files on removable storage devices". This will allow the snap to write to more than just removable devices. If you want to give it access to /home, then enable that switch too.

These are very generalized instructions. I don't run Micropolis from the snap, so don't have personal experience of what switches the devs have enabled. I've pretty much sworn off snaps wherever possible because of issues such as yours.

---

### Post by DuckHook on 2022-03-10
I should add that installing Micropolis via snaps is not the usual way. There's a repo version that tends to be a few releases behind but doesn't require snapd.
```
duckhook@Zeus:~$  apt show micropolis
Package: micropolis
Version: 0.0.20071228-10
Priority: extra
Section: universe/games
Source: micropolis-activity
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,017 kB
Depends: micropolis-data (= 0.0.20071228-10), libc6 (>= 2.29), libsdl-mixer1.2, libsdl1.2debian (>= 1.2.11), libx11-6, libxext6, libxpm4
Homepage: http://www.donhopkins.com/home/micropolis/
Download-Size: 368 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/universe amd64 Packages
Description: real-time city management simulator
 This game simulates building and managing a whole city. The goal of the
 game is to build and design a city. The player can mark land as being
 zoned as commercial, industrial, or residential, add buildings, change
 the tax rate, build a power grid, build transportation systems and many
 other actions, in order to enhance the city.
 .
 Micropolis is the GPL-licensed version of SimCity.

```

---

### Post by DuckHook on 2022-03-10
Further research:

According to my searches, Micropolis hasn't really been developed since 2007, so there is not much difference between the snap and repo versions. No reason to install the snap.

Get rid of it and just go with the repo version.

---

### Post by Objekt on 2022-03-10
The only permissions/interfaces/switches for Snap Micropolis (whether in the Snap GUI or command line) have to do with audio.  No way to do anything with storage, removable or otherwise.

I give up.  I'll try installing Micropolis your way, the Snap version is hopelessly broken.  Thanks!

---

