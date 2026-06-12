---
title: "Opera menu toolbar"
date: 2008-09-29
forum: Desktop Environments
---

### Post by L815 on 2008-09-29
Opera's menu toolbar looks ugly as hell. When a menu is opened, it looks like Win 98, but the rest of Opera is nice and as it should be.

How do I make the toolbar look the way it is supposed to , or at least better?

---

### Post by itbhp on 2008-09-29
You have to install polymer qt3-qtconfig.
Then you have to launch qtconfig-qt3 and select "gui-style" "polymer" and as last thing "tune palette" to set your colors.

Hope this help.

Bye,
 Paolo

---

### Post by juamez. on 2009-01-12
I had the same issue with the toolbar of Opera (QT3), but I'm still not satisfied. It is at least twice as thick as is required by the fonts in it. So a LOT of wasted space.

In windows I could get my Opera smaller than Firefox with compact theme, but in Ubuntu it is simply not possible because of the QT3 toolbar that is much too high.

Does anyone know how to use a thinner toolbar instead?

Is there a way to alter the Polymer skin?

Or should I just use a compact QT3-skin? And where would I find such a skin? I already roamed the internet to find a compact QT3 skin, but so far ... nothing. Maybe I'm not using the righy keywords while searching for a compact QT3 skin?

edit: just for now I have found this sollution which completely hides the menubar and condenses it into one button: [http://ubuntuforums.org/showpost.php?p=5338278&postcount=1094](http://ubuntuforums.org/showpost.php?p=5338278&postcount=1094)
A nice way to further slim things down, but not exactly what I had in mind.

---

### Post by adamlau on 2009-01-12
You can make any toolbar outside of the menu bar (theme controlled) any height you desire. Here are my minimal address and navigation toolbars:

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/OperaMinimalToolbar.png[/IMG]

I can further reduce both toolbar heights if desired, note the use of text only attributes for navigation. Simply decompress the contents of the default skin zip files, review the margin and padding syntaxes and hack away...

---

### Post by urukrama on 2009-01-12
I always hide the toolbar (Alt+F11 by default) and bring it back up whenever I need it, but as mentioned you can change the looks of it by setting a QT theme, either through qt3-qtconfig or kcontrol (if you have KDE installed).

---

### Post by juamez. on 2009-01-28
@adamlau: That looks awesome! But also a little too spartan for me. I'm happy with my breeze simplified micro, but it is the menu bar that is annoying me, which is controlled by qt3-config instead of the opera-skinning module, and it was only the menu bar that I wanted smaller, not the rest of the skin. But thanks anyway. I may be up for some skinning myself if I find it worth it.

@urukrama: Useful tip! I didn't know you could just toggle the menu bar with a keyboard shortcut. I guess I've should've looked some more before complaining.

---

### Post by adamlau on 2009-01-28
The menu bar theme is controlled by the window manager. Here I am using the Variation style under Xfwm (Xfce). Note the difference in pixel height and the improved screen real estate gained over the previous style...

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/OperaMoreMinimalToolbar.png[/IMG]

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/OperaMinimalToolbar.png[/IMG]

---

### Post by juamez. on 2009-05-26
Uhm, I don't know what you mean by the menu bar, but I mean the bar with menu File, Edit, View, Bookmarks, Widgets, Tools and Help. The bar that can be toggled by hitting ALT+F11. That bar. Not the title bar that is indeed changable through the window manager settings.

The problem with this is that I have tried several QT3 styles/themes/whatever, but I never found one that makes said menu bar as slim as it could be.

For example: take Firefox and install Classic Compact theme, and look at how thin the menubar has become. This is what I want with Opera: minimal waste of space.

Can this actually be done with Opera or not? I really dislike Opera in Linux for this.

---

