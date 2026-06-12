---
title: "Computer pauses everithing it's doing after about half an hour."
date: 2006-12-15
forum: Desktop Environments
---

### Post by Tasu on 2006-12-15
Hi all,
Could this be a power management issue? Here's the behaviour...

I'm using edgy.

Whenever my computer does something which do not involve me moving a mouse, the computer stops everything and blanks the screen (like if it puts the screen in standby).
I experienced this behaviour both with ubuntu and xubuntu (so it's not a DE problem) and on two completely different machines (one a AMD Athlon 2.5GHz, 1GB Ram, nvidia geforce 4 mx 440, the other a p2 400Mhz, 128MB Ram and a via video card), so it's not because of my hardware.
For example it happens while I listen music with banshee or rythmbox or beep media player or if I watch a streamed movie throught firefox or using totem or any other media player to watch something. Sot it's not application dependent.
I disabled the screensaver and under power management set that it has to never pause screen nor computer, but the computer still pauses.
If I move the mouse, the music/video/everything starts again from where it was paused!
Really annoying!
Thanx for the help!

---

### Post by Tasu on 2006-12-16
bump!

---

### Post by SleepyHollow on 2006-12-16
Hi,

I made the same observation I really hate this behavior. Now I have disabled all power management settings but I'm not sure if it helps.

Greetings
SleepyHollow

---

### Post by Tasu on 2006-12-16
Thanx for the answer, well! What do you mean by saying you have disabled all power management? have you done something more than putting to never the value of monitor pause and computer pause under the power management application in gnome? Your steps to disable power management do really matter, since changing that obvious values yelded no results to my situation, have you put acpi=off on kernel string? There must be a way to not pause computer if something is playing on it without having to fiddle with kernel params! Something that says (who knows via dbus), "hey! The man is not moving mouse, but c'moooon! I'm playin' that great music album and I know I'm a good computer that won't stop that song in the middle!", this would be some sort of "I computer know that if I play music, videos, streams, etc.. I'm supposed to understand that's not an idle situation just because my owner is not moving around that freaking cursor!" ^_^

^_^

---

### Post by tipping point on 2006-12-16
Tasu, I'm experiencing the annoying "pause" behavior. My power management sliders are also set to "never". The screensaver option is not activated. There must be be some not so obvious setting that we are missing. I have no solution, just wanted to add my comments to your thread. Hopefully someone knows how to stop the "pausing". I'm going to check in on IRC Chat #ubuntu.

---

### Post by tipping point on 2006-12-16
Tasu, this seems to be working no "pause" in over 1 hr. Open your power management preferences.The "general" tab,activate the "always display icon".

---

### Post by Tasu on 2006-12-16
Wow! Thanx for the hint! ^_^ Tomorrow I'll try it and let you know!

---

### Post by Tasu on 2006-12-17
> **tipping point said:**
> Tasu, this seems to be working no "pause" in over 1 hr. Open your power management preferences.The "general" tab,activate the "always display icon".

It works, but this is definitely a bug to be filed, it looks like if you don't click that at least once, it won't apply power management settings.
Just a note, now if you set to never display, it still keeps the power management settings, so if you don't want the tray icon you can remove it, this really seems like an OK button that commits the settings you have chosen.

---

