---
title: "Adding Wine program launchers to AWN bar"
date: 2009-02-15
forum: General Help
---

### Post by Slacker20 on 2009-02-15
I installed Photoshop CS2 and all works well, but I'd like to add the launcher to my AWN bar and still use the same Photoshop icon that Gimp uses.

From Terminal I can run Photoshop with this command:
```
wine start "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
```
However, from within AWN Manager I've tried to add a launcher using that command, but it doesn't add an icon.

I've even tried adding a launcher for Gimp to the AWN bar and then edit it to use the command for Photoshop.  Didn't work.

Any ideas?  Any help would be appreciated,
~Slacker20

---

### Post by rharriso on 2009-02-16
you should try using the absolute path

/home/username/.wine/drive_c/Program Files/...... you can find the rest from there.

---

### Post by Slacker20 on 2009-02-16
```
wine start "\\home\\brandon\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
```

Typing that into Terminal works also, but when trying to add a launcher on AWN with that command, no icon appears.  Usually I've been adding the launchers by adding the shortcuts to the desktop, then dragging them from there onto the AWN bar.  However, that method doesn't work for the Photoshop icon (but it works for Notepad, a Wine program).

Any ideas?

---

### Post by joey-elijah on 2009-02-16
have you tried manually changing the icon for it? In the main AWN preferences window, go to launchers, cselect the CS2 launcher and then edit - click on the 'box' on the left of the dialog that pops up. This will let you choose an icon. You can google or go to deviant-art to find a nice .png icon to use. 

Alternatively you can add a working launcher by *takes breath* making a shortcut in your home folder (or anywhere) to CS2 with the path above. Then drag the shortcut to AWN. THis may possibly keep your icon.. if it doesn't - or it looks pixelated - go back to the shortcut, right click > properties > click the box with the icon in, choose a new icon and try again.

Long winded, but from experience they're what i've used.

---

### Post by Slacker20 on 2009-02-16
> **joey-elijah said:**
> have you tried manually changing the icon for it? In the main AWN preferences window, go to launchers, cselect the CS2 launcher and then edit - click on the 'box' on the left of the dialog that pops up. This will let you choose an icon. You can google or go to deviant-art to find a nice .png icon to use. 

Alternatively you can add a working launcher by *takes breath* making a shortcut in your home folder (or anywhere) to CS2 with the path above. Then drag the shortcut to AWN. THis may possibly keep your icon.. if it doesn't - or it looks pixelated - go back to the shortcut, right click > properties > click the box with the icon in, choose a new icon and try again.

Long winded, but from experience they're what i've used.

[img]http://img.photobucket.com/albums/v655/Slacker_Master17/AWNManager.png[/img]

The icon doesn't appear on the AWN bar when I do that, even though it shows in AWN-manager (and I have clicked refresh, closed, and even restarted computer).  I've never had a problem adding a shortcut to the AWN bar before, but this one is just not wanting to be added.

---

### Post by Slacker20 on 2009-02-16
Ok, despite restarting my computer, the icon wasn't showing up, but after right-clicking on the AWN bar, closing, and then restarting AWN, the icon showed up.  Now I'm having a different issue:

[img]http://img.photobucket.com/albums/v655/Slacker_Master17/Photoshopiconissue.png[/img]

After clicking the launcher icon (the one on the left being highlighted with the cursor), Photoshop opened to a different icon on the right.  Before, I've had no problem getting Photoshop to open and work quickly, but this time it hung on my screen for several minutes, I right-clicked on the icon and tried to close, then a minute or so later it opened.  I then tried opening Photoshop from the Wine menu instead of the AWN launcher and it did the same thing, but it's never acted this way before.

---

### Post by mc4man on 2009-02-16
If you haven't got this resolved a few things I've noticed with the couple of wine apps I have icons for in awn. (and awn in general

When you open something you get 1 icon per window, so if the app has only 1 window you'll only see 1 icon. If it opens 2 windows you'll see 2 icons, ect. This is not wine specific, try gimp. You'll get 2 or 3 icons.

One of my wine apps - Imgburn, usually opens with a detached log, in which case I get 2 icons.
If I disable the 'launch with log', when launched from awn I still get 2 icons, but the 2nd one quickly disappears. Some how awn 'thinks' there will be 2, but then adjusts properly.

Is your photoshop supposed to have a 2nd window that's not showing up?, or is there an option to open multiple windows like gimp does that your not using?



As an aside
I got tired of the whole wine path thing, both from launchers and the command line.
As a solution, that works for the couple of things I run, I've made it so they run like anything else, a 1 word command.

Wine can and does use a 'wine wrapper script' that goes in /usr/bin, the name of the script calls the "same name".exe in drive_c/windows/.

That's why you can use notepad or regedit in the terminal and they open.

So for example I go into Program Files/ImgBurm/, copy ImgBurm.exe to the windows folder and rename imgburn.exe

Then just copying  one of the wrapper scripts in /usr/bin and renaming to imgburn allows ImgBurn.exe to run off of the command imgburn

For something like DVD Audio Creator 1.9.exe I make the .exe in windows creator.exe and the wrapper creator.
(you just need to make sure you don't take a valid unix command or app command,

---

### Post by Slacker20 on 2009-02-16
> **mc4man said:**
> If you haven't got this resolved a few things I've noticed with the couple of wine apps I have icons for in awn. (and awn in general

When you open something you get 1 icon per window, so if the app has only 1 window you'll only see 1 icon. If it opens 2 windows you'll see 2 icons, ect. This is not wine specific, try gimp. You'll get 2 or 3 icons.

One of my wine apps - Imgburn, usually opens with a detached log, in which case I get 2 icons.
If I disable the 'launch with log', when launched from awn I still get 2 icons, but the 2nd one quickly disappears. Some how awn 'thinks' there will be 2, but then adjusts properly.

Is your photoshop supposed to have a 2nd window that's not showing up?, or is there an option to open multiple windows like gimp does that your not using?

Before I had even tried adding the launcher to AWN, opening Photoshop would only bring up one icon, not two.  Now it's as if the icon I created works to load Photoshop, but that's not the icon Photoshop links itself to.

---

### Post by mc4man on 2009-02-16
In dock preferences -> Launchers is there 1 or 2 instances of photoshop?

If I was using full paths in my launcher commands I'd use either of these ways (even though others may seem to work

```
env WINEPREFIX="/home/brandon/.wine" wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
```

```
wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"

```

---

### Post by Slacker20 on 2009-02-17
> **mc4man said:**
> In dock preferences -> Launchers is there 1 or 2 instances of photoshop?

If I was using full paths in my launcher commands I'd use either of these ways (even though others may seem to work

```
env WINEPREFIX="/home/brandon/.wine" wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
```

```
wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"

```

AHHH, thank you!  That second code worked.  I'm only getting one icon showing up when I open Photoshop from the icon, and it started perfectly fine without hanging.

---

