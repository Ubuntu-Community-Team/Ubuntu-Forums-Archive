---
title: "How to put KAlarm icon in Applications &gt; Accessories on Panel?"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Fitzcarraldo on 2007-03-09
Does anyone know if it is possible to get an icon of KAlarm to display in the Panel's pull-down menu Applications > Accessories in Ubuntu Dapper, so that I can launch KAlarm?

I know that KAlarm is designed for the KDE desktop whereas Ubuntu uses the Gnome desktop. But it is still possible to install KAlarm in Ubuntu using Applications > Add/Remove...,  and the note in the Add/Remove window says that KAlarm can be used with desktops other than KDE.

I can launch KAlarm by double-clicking on the executable kalarm in /usr/bin, but it would be nice (and easier) to be able to launch it from Applications > Accessories like other applications.

Anyone able to advise me how to do this by any chance? Thanks in advance.

---

### Post by scottmb on 2007-04-24
Did you ever get an answer to this issue?  I'm facing the same problem!

Thanks,

Scott

---

### Post by Ziggy72 on 2007-04-24
I'm using Feisty with Gnome and I've never used or tried to use KAlarm but I see that in Feisty KAlarm appears in both Add/Remove applications and Synaptic Package Manager. Therefore, there should be no reason why you shouldn't install KAlarm and, having done so, I would expect it to appear somewhere within the Applications drop down menus. If you do install it, and the menu item doesn't appear, it's pretty easy to add a new menu item. Let me know if you need help with this.

---

### Post by Fitzcarraldo on 2007-04-27
*scottmb*,

No, I never did get an answer. I'd still like to know how to do it.

*Ziggy72*,

I'm using Dapper with Gnome, and KAlarm also appears in the Add/Remove applications and Synaptic Package Manager. But, when I installed it, it did not appear within the Applications pull-down menus. I even e-mailed the author of KAlarm, who told me that this was to be expected as the application is written for KDE and not Gnome. It can be launched from the command line or by double-clicking on the executable kalarm in /usr/bin, but I would have preferred to launch it from an icon in the Applications menu.

---

### Post by hellblade on 2007-04-28
Take a look here [http://ubuntuforums.org/showthread.php?t=75606](http://ubuntuforums.org/showthread.php?t=75606)
I don't have gnome installed but I thought there was a menu editor available by right clicking somewhere on the panel.

---

### Post by Ziggy72 on 2007-04-28
Try this to put the program in the Applications menu:
1) Right-click in the space between Applications and Places
2) Left-click Edit Menus
3) Left-click on Accessories in the left hand pane
4) Left click New Item
5) In Create Launcher the type is Application, the Name is KAlarm, the Command is /usr/bin/kalarm (or whatever the executable is).

That should work:)

---

### Post by Fitzcarraldo on 2007-04-29
You're a star, *Ziggy72*. =D>

Step 4 is different for Dapper 6.06 LTS (at least in my case, it is): I had to select 'File' and then 'New Entry' in the pull-down menu. It even let me specify an icon for KAlarm (kalarm.xpm, which Dapper found) by clicking on  the 'No Icon' pushbutton.

Thanks!

---

### Post by Baneblade on 2008-07-07
As Ziggy72 pointed out, you can create items in your drop down menus for programs that dont show up after you have installed them.

"Try this to put the program in the Applications menu:
1) Right-click in the space between Applications and Places
2) Left-click Edit Menus
3) Left-click on Accessories in the left hand pane
4) Left click New Item
5) In Create Launcher the type is Application, the Name is KAlarm, the Command is /usr/bin/kalarm (or whatever the executable is).

That should work"


Its also possible to create desktop icons using the same method for those that prefer them:

1. Right Click Desktop
2. Create Launcher
3. Follow directions from step 5 above.

Hope this helps

---

