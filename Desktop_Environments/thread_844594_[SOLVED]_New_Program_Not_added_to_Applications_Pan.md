---
title: "[SOLVED] New Program Not added to Applications Panel"
date: 2008-06-29
forum: Desktop Environments
---

### Post by burgerearl on 2008-06-29
Pretty complete newbie here...

I set out to install Truecrypt on my ubuntu installation (caveat - I have slow internet and am waiting on an install disk for Hardy, this is on gutsy).

Hitting "add/remove programs" under the applications menu and searching for truecrypt showed no results, so I downloaded the .deb file from truecrypt's website.

I successfully installed the package and can launch truecrypt from the terminal. I also created a launcher that currently resides on my desktop, however, I would like an entry on the applications menu - how can I accomplish this?

Icing on the cake would be correctly associating truecrypt's icon with the launcher.

Thanks!

---

### Post by Wobblybob on 2008-06-29
To create a [launcher] which will run your program from the [Applications] menu, Right click on the [Applications] menu option on the top menu on the desktop. Select [Edit Menus] then select the main category for your program ie [Internet] and then the [+New Item] Button from the Right Hand menu. Add the following:

[Type] leave as Application
[Name] The Name you want to show on the menu.
[Command] The path to the program i.e /home/user/myprogram 
[Comment] A description that will show when you hover over the menu item.

[as you have a launcher on your desktop you could check it's properties.]

You can then amend the icon if you either don't like the default that the program has added or if there is no program icon available. Click on the icon in the top left corner and navigate through the default options

---

### Post by burgerearl on 2008-06-29
Thanks for the quick reply. This was exactly what I was looking for.

I should have been more specific with my icon question:

I understand the dialog to change the icon, however, I have no idea where to locate the truecrypt icon. I know it exists (it puts a widget with the correct icon up next to tracker in the system tray).

I searched to try and figure out where the icon might reside but I'm totally lost.

---

### Post by Wobblybob on 2008-06-29
> **burgerearl said:**
> 
I searched to try and figure out where the icon might reside but I'm totally lost.

you could try navigating here /usr/share/pixmaps I don't have this installed so can't give you a better option but most apps install icons here or in one of the sub folders.

---

### Post by burgerearl on 2008-06-29
Truecrypt didn't copy an icon to pixmaps by default, but I found one here: [http://www.dailygyan.com/2008/03/truecrypt-icon-for-ubuntu.html](http://www.dailygyan.com/2008/03/truecrypt-icon-for-ubuntu.html)

Copying the icon to pixmaps caused the launcher to automatically update it's icon. Great!

Thanks for the help, problem solved!

---

