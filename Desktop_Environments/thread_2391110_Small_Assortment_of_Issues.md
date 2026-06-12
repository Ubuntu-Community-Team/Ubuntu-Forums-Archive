---
title: "Small Assortment of Issues"
date: 2018-05-05
forum: Desktop Environments
---

### Post by pD43WfR on 2018-05-05
Hello there! A few days ago I decided to give Ubuntu Budgie 18.04 a go. So far it's been pretty great, but there's a few things that are really annoying that are bugging me that I'd like to figure out how to deal with



[LIST=1]
[*]Pressing F12 opens up some kind of terminal from the top of the screen. This is getting annoying as with Steam F12 is the default screenshot button and I prefer it that way. I would like to disable this, but I can't find where to do this. Is this what's referred to as "Quake"? ( If so I appreciate the nod to a classic game :D )
[*]My desktop shortcuts (.desktop files) don't have any custom icons. I can't set custom icons. When I install Steam games, they create desktop shortcuts, and I would like to actually see my game icons. Even when I try to set them manually, nothing happens.
[*]When an application is "not responding" for about 5 seconds Budgie (I believe GNOME does this too) pops up saying "BLABLABLA APPLICATION" is not responding. This happens in particular every single time I launch some games that have an initial loading screen period. Then the game gets minimized because of this dumb popup. How can I extend the timeout period for this popup or disable it entirely?
[*]Whenever I reboot\power on my computer, the default sound output device keeps changing back to what it was before I set it to the output I want it to use. How can I save the default sound output device? This is getting really annoying to deal with all the time.
[/LIST]

Here's an Imgur album with screenshots of what I'm referring to above: [https://imgur.com/a/khXFiuo](https://imgur.com/a/khXFiuo)

If somebody could please help me with these issues, I'd greatly appreciate it.

---

### Post by kerry_s on 2018-05-06
1. settings->devices->keyboard
2. right click *.desktop file-> properties-> click on the little picture. *.desktop files need to also be executable, so do that on the permissions tab while your in properties. finally click on it & select trust.
3. don't know
4. not sure, maybe pactl?

---

### Post by pD43WfR on 2018-05-06
> **kerry_s said:**
> 1. settings->devices->keyboard
2. right click *.desktop file-> properties-> click on the little picture. *.desktop files need to also be executable, so do that on the permissions tab while your in properties. finally click on it & select trust.
3. don't know
4. not sure, maybe pactl?

1: Ah, I didn't realize there were MULTIPLE keyboard shortcuts for it for some reason
2: As I explained, this does not work. I keep trying to set the icon, nothing happens.
3: R.I.P.
4: ...I know most Linux people don't want to hear this, but is there a non-terminal way to do this? This just sounds like such a basic feature that it doesn't make sense for it to not exist.

---

### Post by pD43WfR on 2018-05-06
Sorry to double post, but I forgot to mention this earlier. When right clicking on a file\folder and clicking "Properties" I can only move the "Properties" window and I can't click or move anything in the parent window, or the window I started from.

---

### Post by davidmohammed on 2018-05-06
> **pD43WfR said:**
> Sorry to double post, but I forgot to mention this earlier. When right clicking on a file\folder and clicking "Properties" I can only move the "Properties" window and I can't click or move anything in the parent window, or the window I started from.

sounds like you have the option "Attach modal dialogs" ticked in budgie-settings - windows.  Suggest untick and reboot.

---

### Post by davidmohammed on 2018-05-06
for point 3 - looks like GNOME have hard-coded this for 5 seconds [https://askubuntu.com/questions/412917/how-to-increase-waiting-time-for-non-responding-programs](https://askubuntu.com/questions/412917/how-to-increase-waiting-time-for-non-responding-programs)

---

### Post by davidmohammed on 2018-05-06
re point 4 - anything here that helps? [https://askubuntu.com/questions/398030/change-default-sound-device](https://askubuntu.com/questions/398030/change-default-sound-device)

Looks like GNOME doesn't really hand hold you here - so a bit of fiddling behind the scenes is required.

---

