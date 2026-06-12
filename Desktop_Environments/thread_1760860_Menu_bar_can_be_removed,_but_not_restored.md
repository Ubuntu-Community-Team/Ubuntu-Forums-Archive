---
title: "Menu bar can be removed, but not restored??"
date: 2011-05-17
forum: Desktop Environments
---

### Post by GNUbee40 on 2011-05-17
Hey!

I know, I know - the new Ubuntu 11.04 is out, so why am I still stuck with 10.10? Well, never update, when in the middle of a project. You might run into trouble and spend valuable time you don't have!:P

But to the point. In 10.10 I recently came to remove the menu bar. A right click and left click at the wrong time - and gone!
I was then amazed that there is no way to get it back! :o
It seems the only way to restore settings is to delete them all together and start from scratch. Thus, renaming ~/.gconf/apps/panel and logoff/logn brings about a new panelfolder, and a new panel with menu bar - but of course without any of my custom objects :(

These objects are stored as xml additions in subfolder of my backed up ~/.gconf/apps/panel/objects. However, copying these folders over in the new ~/.gconf/apps/panel doesn't bring any luck.
The xml additions representing my custom icons are NOT integrated in the new panel.:confused:
Similarly, copying the menu_bar_screen0 folder from the new ~/.gconf/apps/panel to the old one, would not restore the menubar.

There must be a master xml file somewhere else. Maybe the %gconf file in the panel folder (every subfolder of .gconf has a file named %gconf). After I renamed this file in the old ~/.gconf/apps/panel, almost all other %gconf's in the subfolders were changed, and now I now longer can restore the old panel, even though the folders containing my panel bar objects still exists - and these remained unchainged altogether.

If there is anyone who can shed some light on how you might save your custom settings I would be quite grateful.

Maybe the situation will be wholly different with 11.04?

Regards

---

### Post by wildmanne39 on 2011-05-17
> **GNUbee40 said:**
> Hey!

I know, I know - the new Ubuntu 11.04 is out, so why am I still stuck with 10.10? Well, never update, when in the middle of a project. You might run into trouble and spend valuable time you don't have!:P

But to the point. In 10.10 I recently came to remove the menu bar. A right click and left click at the wrong time - and gone!
I was then amazed that there is no way to get it back! :o
It seems the only way to restore settings is to delete them all together and start from scratch. Thus, renaming ~/.gconf/apps/panel and logoff/logn brings about a new panelfolder, and a new panel with menu bar - but of course without any of my custom objects :(

These objects are stored as xml additions in subfolder of my backed up ~/.gconf/apps/panel/objects. However, copying these folders over in the new ~/.gconf/apps/panel doesn't bring any luck.
The xml additions representing my custom icons are NOT integrated in the new panel.:confused:
Similarly, copying the menu_bar_screen0 folder from the new ~/.gconf/apps/panel to the old one, would not restore the menubar.

There must be a master xml file somewhere else. Maybe the %gconf file in the panel folder (every subfolder of .gconf has a file named %gconf). After I renamed this file in the old ~/.gconf/apps/panel, almost all other %gconf's in the subfolders were changed, and now I now longer can restore the old panel, even though the folders containing my panel bar objects still exists - and these remained unchainged altogether.

If there is anyone who can shed some light on how you might save your custom settings I would be quite grateful.

Maybe the situation will be wholly different with 11.04?

Regards

Hi, If you move your mouse to where the menu bar was and right click you can choose to add new panel.

---

### Post by Frogs Hair on 2011-05-17
If you have removed the panel add a new panel as mentioned . To restore panel applets to default run the following code or add the applets manually by right clicking the panel and selecting the items from the add to panel menu.
```
gconftool --recursive-unset /apps/panel && killall
```

---

### Post by GNUbee40 on 2011-05-17
Wouw guys - quick response :popcorn:

Thanks a lot.

However,
Adding a new panel is NOT what I want to do here, neither resetting everything and start all over.
Admittedly, Frog Hair's method for doing the latter is somewhat more elegant than deleting all the folders :)
I'd also like to point out I had no difficulties with any applets. It is the Launchers I had made on the old panel, I'd like to preserve.

What I want is to re-add the (accidently removed) main menu (Applications, Places, System) *in its original form* to an existing, customized panel.
I cannot do that when right clicking and choosing "Add to panel..." The main menu offered there is just a little icon button, a drawer if you will, not the original main menu.

:confused:

---

### Post by Frogs Hair on 2011-05-17
There are two menu options on the add to panel menu , the one you want to restore is Menu Bar ( a custom menu bar ). The other offers a single icon.

---

### Post by GNUbee40 on 2011-05-17
Embarasssing ](*,)

Actually you CAN add the main menu by right clicking on the panel, then choose  "Add to panel..." and choose the right item on the list. 
The right item was just labled so ODDLY as a userdefined menu and with no visible icon (white on white) that I would not have suspected it to be the main menu. :roll:
This is true for the Danish translation, I sure hope the english lable is less ambiguous - but as I see just know thanks to Frogs Hair, it is not. 
When I read "Custom Menu Bar" I read "make your own menu bar" which is not what I wanted. Clearly mislabelled.

Sorry for wasting people's (and my) time. :oops: Thanks for the help.

Regards

---

### Post by Frogs Hair on 2011-05-17
There are no stupid questions here and others may learn from post .:D

---

### Post by wildmanne39 on 2011-05-18
> **GNUbee40 said:**
> Embarasssing ](*,)

Actually you CAN add the main menu by right clicking on the panel, then choose  "Add to panel..." and choose the right item on the list. 
The right item was just labled so ODDLY as a userdefined menu and with no visible icon (white on white) that I would not have suspected it to be the main menu. :roll:
This is true for the Danish translation, I sure hope the english lable is less ambiguous - but as I see just know thanks to Frogs Hair, it is not. 
When I read "Custom Menu Bar" I read "make your own menu bar" which is not what I wanted. Clearly mislabelled.

Sorry for wasting people's (and my) time. :oops: Thanks for the help.

Regards
Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.):P

---

### Post by GNUbee40 on 2011-05-18
Oh yes - will do.

Would be interesting to know, though, if one could save or move launcherobjects and applet settings to a new panel bar, f.ex after reinstall. 
I reckon if I save the whole panelbar folder (the whole xml tree) it will work, but it seems you cannot backup just the launchers or applet settings. In gconf-editor, it seems you cannot save, copy or duplicate keys from different parts of the trees, only edit the values.

Cheers

---

### Post by Krytarik on 2011-05-18
You can save/restore specific Gconf keys/trees to/from an XML file.

To save, the Gconf path is just an example:
```
gconftool-2 --dump /apps/panel/objects > FILENAME
```
To restore:
```
gconftool-2 --load FILENAME
```
Greetings.

---

### Post by GNUbee40 on 2011-05-23
:guitar:

Nice! This will be part of my backup routine then :)

Thanks for the help!

---

