---
title: "Azureus opening behind existing windows"
date: 2008-09-03
forum: Desktop Environments
---

### Post by pterosky on 2008-09-03
When I click on a torrent link on a web site or press the shortcut I have defined to open Azureus, it launches behind the already opened windows, in stead of stealing focus, which would be the logical thing to do.

I could swear that Amarok behaves the same way, but I can recreate the behavior right now...

Does anyone know how to tell Azureus to steal focus when either the user clicks on a torrent link or relaunches it via a shortcut?

---

### Post by pterosky on 2009-03-04
I have since switched back to Transmission, which shares the problem of not being "always on top". I have found this solution that at least puts Transmission on top when adding a new torrent even though the "add torrent" dialog isn't...

The example will set as rule that Transmission and Audacious are to be above other windows when activated. Audacious won't be "always on top" when using the "Global Hotkey" plugin's shortcut to toggle Player Window to open it from the tray.

Go to System -> Preferences -> Advanced Desktop Effects Settings.

Enable and click on "Window Rules" under "Windows Management".

Select "Enable Window Rules" and click on the plus sign after the "Above" text field to add a new rule.

Click on "Grab" and click the already open Audacious program.

Repeat with Transmission -- remember to select the relation "or". The result should be:

```
(class=Audacious) | class=Transmission
```

The "|" meaning "or".

Log out and in: The programs should now be able to get focus in stead of being hidden behind other already open programs and windows.

---

