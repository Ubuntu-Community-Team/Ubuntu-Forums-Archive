---
title: "Pressing superkey doesn't open the dash"
date: 2013-12-25
forum: Desktop Environments
---

### Post by kristoffer.alfh on 2013-12-25
[I]First post, please be nice. :)

[/I]The title is pretty self-explanatory; when I press the superkey, the dash doesn't open. When I hold the key down, the "Keyboard Shortcuts"-window pops up, so there's nothing wrong with my keyboard. When I use the pointer and click the launcher(?) button manually, the dash opens.

This problem started occurring a few days ago, but I have no clue as to what could have triggered it.

I have done some googling, but can't seem to find any solution.

I'm running Ubuntu 13.10. If any additional information regarding my system is needed to debug this, please let me know.


Thanks for any help you can provide!


*Off-topic: Is it possible to change my username here on Ubuntu Forums?*

---

### Post by deadflowr on 2013-12-25
When you mouse click on the desktop area, then can you open the dash with the superkey?
Have you installed anything that changes settings, like ccsm or unity-tweak-tool?

Also, go to the resolution center to request a name change
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)
read the sticky on top.

---

### Post by kristoffer.alfh on 2013-12-25
Thanks for replying.[I]

When you mouse click on the desktop area, then can you open the dash with the superkey?
[/I]No.[I]

Have you installed anything that changes settings, like ccsm or unity-tweak-tool?[/I]
I have installed both of those. I have tried to tweak some of those settings, but nothing seems to work.

---

### Post by deadflowr on 2013-12-25
When you hold the launcher down(and the keyboard shortcuts overlay shows), do you get numbers on the launcher icons in the launcher?
It would be blank for the dash, and then each launcher would have a number on it, starting with one and going down to 10,(zero).
Depending on how many you have in the launcher. With ten launchers having numbers.(ie, the top ten apps).

---

### Post by kristoffer.alfh on 2013-12-25
Yup, those numbers do appear.

Also, pressing the superkey plus another key works. For instance, I have Super + L assigned to lock the screen, which does work fully.
However, assigning only Super to a keyboard shortcut does not work (in Settings -> Keyboard -> Shortcuts). When I try to do this, the shortcut just clears as if I'm pressing backspace. (I don't know if it's supposed to be like this, but)

---

### Post by deadflowr on 2013-12-25
Does super + A open the dash apps section, as it should?
Or super + F for files, or super + V for videos.

Seems odd that all has worked as it should, except the stand alone super = dash.

---

### Post by kristoffer.alfh on 2013-12-25
Super + A, Super + F and Super + V all work as they should.

It really is odd.

---

### Post by mc4man on 2013-12-25
I would log in to the guest session & see if it works there.

---

### Post by kristoffer.alfh on 2013-12-25
It does work in the guest session. So I guess I have screwed up some settings, but I have no idea what it could be.

---

### Post by kristoffer.alfh on 2013-12-25
Update:
After getting confused by some weird audio-related problems (all audio magically stopped working), I  decided to backup my home folder and reinstall Ubuntu (previous install was only about two weeks old, so it wasn't really that big of a deal for me). Now everything's  working well. *whew*

---

### Post by mc4man on 2013-12-25
In the future, if you want to mess around with settings, bindings, ect. you can add a new user & fool around there. That way no issue dumping that user if things get messed up.
There is a command or 2 to reset most settings back to default, I haven't kept up on but sure others have (depends on Ubuntu release.

---

### Post by deadflowr on 2013-12-25
> **mc4man said:**
> In the future, if you want to mess around with settings, bindings, ect. you can add a new user & fool around there. That way no issue dumping that user if things get messed up.
There is a command or 2 to reset most settings back to default, I haven't kept up on but sure others have (depends on Ubuntu release.

I usually end up resetting through ccsm.
Just go to preferences, and then click reset to defaults.
It's always important to note that resetting makes the system look like it is exploding, and to be patient, it will come back.

If you reset the ccsm, then when it finally settles, re-enable the various settings.
Most notably the unity plugin, it always disables when this method is used.
But sometimes I've seen Desktop Wall and/or window decorations disabled.

That said, re-installing the system is some kind of workable solution.
When I first installed Ubuntu I think I re-installed daily for the first two weeks.
But that might have been my initial joy at the speed of the install, topped with my utter lack of understanding about the system, in general.
Still feel like I know Jack Squat about the system, but now I know a few things to do and not to do, for the most part.
And how to do very remedial repair work if needed.

---

### Post by kristoffer.alfh on 2013-12-26
Thanks for the tips. :)

---

