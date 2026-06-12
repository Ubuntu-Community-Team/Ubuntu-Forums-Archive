---
title: "Where did Window Maker's window switching panel go? I miss it!"
date: 2007-02-20
forum: Desktop Environments
---

### Post by blue_puyo on 2007-02-20
I'm fresh off the Gentoo boat where life was sweet when it worked and impossible when it didn't. Common story I think.

Using Window Maker, I notice that the "window switching panel" doesn't display like it did in Gentoo. Under Gentoo, this little blue window with the current desktop's windows' icons displayed in a row would pop up when I presset Alt+Tab to cycle through windows.

I also notice that the option to use "Windoze" style cycling isn't where it normally is in WPrefs, and also that wmakerconf explains that the popup window during window cycling is only displayed if "Windoze" style cycling is enabled.

Both Ubuntu and Gentoo wmaker versions == 0.92, the latest at the time of writing.

My best guess at the moment is that Ubuntu wmaker wasn't compiled with Windoze cycling available.

Is this a Window Maker thing, and Ubuntu thing, some combination, or is it just some configuration setting that I'm missing?

---

### Post by blue_puyo on 2007-09-18
Aaah. I went to the trouble of running wmaker under xinit and gdb in order to track down the problem. Took me 2 hours but on reflection the problem was quite obvious.

Window Maker expects the files swtile.png and swback.png to be in its Pixmap search path (one of the tabs in WPrefs is for setting paths). I didn't even notice that most of mine were broken because it's tucked away in WPrefs and not something you immediately notice. They looked like this on Gentoo:

  /usr/share/X11/WindowMaker/Pixmaps
  ...

but they should look like this, on Ubuntu:

  /usr/share/WindowMaker/Pixmaps

The Ubuntu wmaker package installs swtile.png and swback.png in /usr/share/WindowMaker/Pixmaps so as long as that's in your pixmap search path, even if the others are broken, the switching panel should load the graphics and function correctly.

---

### Post by soops1966 on 2007-10-18
I've got a problem with keyboard shortcuts:

They just don't work. All the default ones are missing too. I've created a new user and they're missing there too, so I know it's not my settings.

I did a clean install to Feisty, I was a happy user of Dapper before so I'm a bit gutted that WM just doesn't work right.

I've loooked everywhere for a cluestick so any help would be very welcome.

---

### Post by marduk7 on 2008-02-02
> **blue_puyo said:**
> Aaah. I went to the trouble of running wmaker under xinit and gdb in order to track down the problem. Took me 2 hours but on reflection the problem was quite obvious.

Window Maker expects the files swtile.png and swback.png to be in its Pixmap search path (one of the tabs in WPrefs is for setting paths). I didn't even notice that most of mine were broken because it's tucked away in WPrefs and not something you immediately notice. They looked like this on Gentoo:

  /usr/share/X11/WindowMaker/Pixmaps
  ...

but they should look like this, on Ubuntu:

  /usr/share/WindowMaker/Pixmaps

The Ubuntu wmaker package installs swtile.png and swback.png in /usr/share/WindowMaker/Pixmaps so as long as that's in your pixmap search path, even if the others are broken, the switching panel should load the graphics and function correctly.

I came across the same problem (non-displaying windows switching panel) with clean install of WindowMaker on Ubuntu 7.10. /usr/share/WindowMaker/Pixmaps is already in pixmaps search path. I'm going to file a bug...

---

### Post by marduk7 on 2008-02-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/wmaker/+bug/161792](https://bugs.launchpad.net/ubuntu/+source/wmaker/+bug/161792) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Actually there is a bug and workaround is also described there
[https://bugs.launchpad.net/ubuntu/+source/wmaker/+bug/161792](https://bugs.launchpad.net/ubuntu/+source/wmaker/+bug/161792)
> - Install wmakerconf
- start wmakerconf
- go to 'shortcuts'
- look for 'switch input focus to the next window'
- set mod1-tab as shortcut

---

