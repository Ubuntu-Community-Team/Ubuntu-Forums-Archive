---
title: "Ubuntu Logo Problems"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Stambo00 on 2006-06-04
Please help me before I go insane!

I'm trying to change the ubuntu logo beside the applications menu to the gnome foot. 

Ive tried changing both:
/usr/share/icons/Human/42x48/places/start-here.png
and
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

I have all the default settings on a freshly installed dapper.

Ive had this same problem on every release of ubuntu I've had.

Any suggestions?

---

### Post by oyvindaa on 2006-06-04
[There](http://ubuntuforums.org/showthread.php?t=167658&highlight=gnome+foot) you go mate :)

---

### Post by Stambo00 on 2006-06-04
The first suggestion on the link doesnt work for me!

I tried the second suggestion further down the page but have a little trouble understanding it?

Could you help me out?

---

### Post by oyvindaa on 2006-06-04
This is what I think they mean:

System Tools --> Configuration ..

Once in there, go to /apps/panel/objects/object_0 (it's object_0 on mine, and you can see that because the object type is 'menu-object').

Then right click on "Use custom icon" --> New Key .. call it "custom_icon" and save it as a string. Put the location of the new icon as the key value.

For the gnome-foot, use this:

/usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png

For it to work, you have to click on the little square on the right side of "use_custom_icon".

Then log out, and log back in. (I didn't even have to do that).

Hope you sort this out mate, tell me how it goes.

---

### Post by Stambo00 on 2006-06-04
Unfortunately it still didnt work! Even when i rebooted.

In my objects section I have:

browser_launcher_screen0
object_0
object_1
object_3
session_dialog_screen0

I created the string file in "object_0"

I appreciate you trying to help me.

What should I do now?

---

### Post by oyvindaa on 2006-06-04
Alright. 

If you followed all my instructions above and it still didn't work, then I'm afraid I can't help you mate :(

Maybe someone else can?

---

### Post by Stambo00 on 2006-06-04
What do you mean by menu object? Is that what I should be calling the string?

How can I tell which is menu object?

---

### Post by Denis on 2006-06-04
I'm also trying to change the menu logo, but without succes so far. 

I tried changing the icon with gconf, but that didn't work. I think the problem is that my menu has the "menu-bar" object_type instead of the "menu-object" type.

When I add a "main menu" to the panel, the type is "menu-object", but that's something different, it's just a single button. This icon can indeed be changed. 

I can change the type of the real menu to "menu-object" in the editor, but then it just changes to a button.

Added a screenshot to make it more clear

---

### Post by oyvindaa on 2006-06-04
[QUOTE=Stambo00]What do you mean by menu object? Is that what I should be calling the string?[/QUOTE]

No, when you've opened the configuration tool and browsed your way into: /apps/panel/objects/object_0/ you can see that the object_type is a menu-object.

What you call the string isn't important, I just called it 'custom_icon'.

The path you put in the option below is important though, as it is the path to your new icon.

---

### Post by oyvindaa on 2006-06-04
[QUOTE=Denis]
When I add a "main menu" to the panel, the type is "menu-object", but that's something different, it's just a single button. This icon can indeed be changed. 
[/QUOTE]

Stambo00, have you done it this way or do you have the original Ubuntu menu?

If you got the original one, that might explain why it isn't working.

[IMG]http://i35.photobucket.com/albums/d163/oaa/gnome-foot-menu.jpg[/IMG]

Mine's like that.

---

### Post by Stambo00 on 2006-06-04
My applications menu turned into a single icon of the gnome foot.

So how to I now get this to change the applications icon instead?

This is doing my head in!

---

### Post by Denis on 2006-06-04
It looks like this methon can't be used with the default menu (with Applications, Places and System on it) :(

I did notice that this icon can be changed when changing the **theme**. For example, I've got the tango icon theme [edit]Tango noir[/edit], which uses the gnome foot as the icon. I've tried changing the themes by hand, but I didn't succeed in changing the logo, most themes just use the Ubuntu logo. I'm a bit confused as I don't know where these themes get that logo.

---

### Post by Stambo00 on 2006-06-04
OK, depending on the theme I'm using It seems I might be stuck with the ubuntu logo if its a menu-bar object? Changing the icon theme has helped solved this problem. But its annoying that I can't seem to configure the icon if I'm using the human themed icons.

---

### Post by Denis on 2006-06-04
I don't get it, I replaced every "start-here" and "distributor-logo" with the gnome foot (except those of the Tango and Tangerine themes). All the icons in the Human theme (/usr/share/themes/Human/*) are changed too. 

But the panel still shows The Ubuntu logo ](*,) Where does that logo come from...?

I rebooted and tried gtk-update-icon-cache (this has something to do with the cache I think). But the Ubuntu logo remains the same.

---

### Post by Stambo00 on 2006-06-04
I found that using any theme besides human, tango (and something else, i forgot), let you change the icon to the gnome foot. Yeah, I would like to know where this icon is residing on the system?

---

