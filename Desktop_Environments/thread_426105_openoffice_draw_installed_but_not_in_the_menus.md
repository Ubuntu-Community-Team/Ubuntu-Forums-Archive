---
title: "openoffice draw installed but not in the menus"
date: 2007-04-28
forum: Desktop Environments
---

### Post by Nirro on 2007-04-28
Hi, It took me some time to find the correct command to launch open-office draw.

Why doesn't it appear in the menus ?

I'm using Feisty.

Thanks.

---

### Post by Sef on 2007-04-28
> Hi, It took me some time to find the correct command to launch open-office draw.

Why doesn't it appear in the menus ?

I'm using Feisty.


System > Preferences > Main Menu > Graphics > click on Open Office Draw > click on close.   It will be under your graphics menu.

---

### Post by blackened on 2007-04-28
Go to System->Preferences->Main Menu
Select the Office menu and in the right pane select New Item. The "Create Launcher" dialog likes to spawn behind the main menu window, so watch the taskbar for it to appear.

Ok, in the dialog that comes up enter this:
```

Name: OpenOffice.org Draw
Command: ooffice -draw %U

```

Put whatever you want in the comment section.
The icon is /usr/share/icons/hicolor/48x48/apps/ooo-draw.png

---

### Post by blackened on 2007-04-28
It's not listed as a hidden item in my main menu, might not be in his either.

---

### Post by Nirro on 2007-04-28
Yeah, Thanks guys.

But the question is why isn't it in there by default, maybe it's in purpose ?

Do you think it worth opening a bug-report for this ?

---

### Post by blackened on 2007-04-28
I couldn't tell you exactly why it's not there. Maybe they just overlooked it, though I wouldn't really consider that a bug.

---

