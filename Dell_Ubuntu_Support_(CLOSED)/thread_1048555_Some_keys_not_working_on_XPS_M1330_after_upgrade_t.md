---
title: "Some keys not working on XPS M1330 after upgrade to Intrepid"
date: 2009-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tentotwo on 2009-01-23
I had an annoying keyboard problem after upgrading to Intrepid on my XPS M1330. All the keys would be mapped fine in the Gnome login screen, but once on the desktop, some keys wouldn't work at all (left, right, down) or would exhibit really strange behaviour. To get the at-symbol on my german keyboard, I normally have to press the right "alt" key + "q", but this would not yield any results. Instead, I had to press and hold the right "alt" key, then press and release "shift" and finally press "q". Other keys specific to the German keyboard layout, like "ä" and "ö" worked fine, indicating that the correct layout was selected.

One way to get the keys to work was to change the keyboard model in "System"/"Preferences"/"Keyboard"/"Layouts", it didn't matter wether I chose "Dell", "Generic 101" or "Generic 104", all of them worked without difference. After logging out and in again, the previously selected and working model would still be active, but the weird behaviour was back again.

Searching the forums and the web for solutions revealed that there are a lot of different problems with keyboard layouts with a plethora of different suggested solutions.

One which I found to work was to call "setxkbmap de" after logging in. Note, however, that the German keyboard was indeed loaded correctly without calling setxkbmap, albeit with the abovementioned mapping errors.
I have now set the command to run automatically in "Systems"/"Preferences"/"Sessions". Not a very elegant solution, but one that works fine for me. Maybe this helps others as well (I've described the problem so detailed to make it easier to search for). If anyone has an idea to solve this problem without the shoddy workaround, I'd be glad to try it out.

---

