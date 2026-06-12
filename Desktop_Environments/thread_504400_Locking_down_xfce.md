---
title: "Locking down xfce"
date: 2007-07-19
forum: Desktop Environments
---

### Post by Falc on 2007-07-19
I am co-responsible for a small cybercafé. I am trying to lock down a Xubuntu setup in such a way that the users basically cannot change anything about it and only have access to Firefox. I have read the XFCE docs and tried to use their kiosk functionalities, but I have run into some issues. Hopefully you can help.

1) Locking down the panel with the CustomizePanel setting simply freezes it into the default setup. This is not an acceptable setup since the XFCE menu is available. What file would I need to edit to modify this default panel layout?

2) When I let XFCE manage my desktop, the right-click menu gives access too way too many settings. But when I don't let XFCE manage the desktop, the background I use gets removed. Is there a way to either remove the right-click menu from XFCE? Failing that, where do I change my desktop background when XFCE isn't managing it?

Thanks in advance

---

### Post by mojoman on 2007-08-23
On  #2: In the menu, go to Settings -> Desktop Settings. There is a tab called "Behavior" where you can uncheck "show desktop menu on right click". This is also where you check or uncheck "Allow Xfce to manage the desktop". Under the tab "apperance" you can check the box "show image" and then type in the path to whatever background you wish to use. You can disable menu on right-click, use your own background and still let Xfce manage the desktop (or any combination thereof)

Does this solve the problems under #2?

I'll try to get back to you on #1 later but right now I don't have the answer to it.

Best regards
mojoman

---

### Post by tra4d on 2008-03-18
Falc

Were you successful?  I am trying to do the same and have tried to do what is suggested here but there are still ways around this (i.e. right-click on a desktop icon - I have a desktop icon to reopen the dedicated application in case it get shut down - and you get all kinds of goodies.

Thanks,
Scott

---

