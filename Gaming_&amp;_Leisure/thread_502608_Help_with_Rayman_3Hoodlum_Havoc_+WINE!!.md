---
title: "Help with Rayman 3:Hoodlum Havoc +WINE!!"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by GhostZrydA on 2007-07-16
-

---

### Post by cogadh on 2007-07-16
Try adding a registry edit to allow direct hardware access:
[LIST=1]
[*]From the terminal, run "regedit"
[*]In the file tree, browse to "HKEY_CURRENT_USER\Software\Wine"
[*]Right-click in the right hand pane and select New > Key
[*]Name the new key "Alsa Driver" (no quotes)
[*]Again in the right hand pane, right-click and select New > String Value
[*]Name the new string "UseDirectHW" (no quotes)
[*]Double-click on the new string and set it to "y" (no quotes)
[/LIST]
Exit the registry editor and try re-running the game.

---

### Post by GhostZrydA on 2007-07-17
-

---

### Post by cogadh on 2007-07-17
You guessed right, that's exactly where it goes. Sorry, I should have made that a little more clear.

Try upping the rate to 44100, I wouldn't recommend anything lower than that. If that doesn't work, try the different accelleration settings with and without "Driver Emulation" checked (it might take a little while to try all the options).

---

### Post by GhostZrydA on 2007-07-17
-

---

### Post by cogadh on 2007-07-17
I recommend doing it even if it doesn't fix the sound issue. When you run the game from the terminal, run it like this:
```
WINEDEBUG=-all wine game.exe
```
Obviously change the exe name to match your game. This will supress all of the error messages that are normally produced when Wine is run and can help improve performance.

You might also check the in-game settings for any sound settings that can be changed or reduced, that may help.

That being said, I checked Wine's AppDB entry for the game and it appears that it has a history of audio problems, particularly with speech. This could be one of those games that has inherent problems with Wine:
[http://appdb.winehq.org/appview.php?iVersionId=6265](http://appdb.winehq.org/appview.php?iVersionId=6265)
Don't let the gold rating fool you, based on the poster's description, the game should not have been rated any higher than silver. I'm surprised the app maintainer let it through with a gold rating.

---

### Post by GhostZrydA on 2007-07-17
-

---

