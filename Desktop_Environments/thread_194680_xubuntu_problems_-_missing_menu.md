---
title: "xubuntu problems - missing menu"
date: 2006-06-11
forum: Desktop Environments
---

### Post by elpresidente on 2006-06-11
I recently checked out xubuntu (xfce4) and was impressed enough to want to switch to it (typically I use fluxbox and sometimes gnome). I've apted xubuntu-desktop on 3 of my pcs. I have encountered strange problems on a couple of them. One - I started nautilus from within xfce - it changed the background etc, so I promptly killed it but never regained the menu (right-click or on the top bar).  The same thing happened on another box when I was changing user interface settings, desktop settings and attempting to edit the menu. I was unable to bring up the menu to edit and after close that utility, menu functionality was gone. I think there must be a quick way to get back the menu or avoid it happening (like nautilus with no-desktop option) but am unable to find what it is on either ubuntuforums.org or google.com. Reboots don't bring it back.

Any suggestions?

---

### Post by bbzidane on 2006-06-11
just want to say the exact same thing happened to me
right click on desktop stopped doing anything
and my menu is empty

hope someone can provide a solution to this

---

### Post by bbzidane on 2006-06-11
i fixed my right click menu problem
i just copied back the original menu into my local config directory and that fixed that

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

---

### Post by elpresidente on 2006-06-11
[QUOTE=bbzidane]i fixed my right click menu problem
i just copied back the original menu into my local config directory and that fixed that

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```[/QUOTE]

Thanks much! That did the trick. I had run a locate for menu.xml with the same idea but I guess I glanced over the output to quickly.

Thanks again. I'm liking xfce4.

---

### Post by elpresidente on 2006-06-11
Also, the font is not right. I thought I would be able to change it back to default after I got the menu back but no luck. Anyone know how to get the font back to default??

Looks like this:
[http://www.brussow.net/stuff/screenshot_fonts.jpg](http://www.brussow.net/stuff/screenshot_fonts.jpg)

---

### Post by psychicdragon on 2006-06-11
[QUOTE=elpresidente]Also, the font is not right. I thought I would be able to change it back to default after I got the menu back but no luck. Anyone know how to get the font back to default??

Looks like this:
[http://www.brussow.net/stuff/screenshot_fonts.jpg](http://www.brussow.net/stuff/screenshot_fonts.jpg)[/QUOTE]
The default font is 'Sans 9'.

RE: The menu editor.
This bug has been discussed quite a bit on the xubuntu-devel mailing-list. A patched xfdesktop4 package should show up in dapper-updates any time now.

---

### Post by elpresidente on 2006-06-12
[QUOTE=psychicdragon]The default font is 'Sans 9'.

RE: The menu editor.
This bug has been discussed quite a bit on the xubuntu-devel mailing-list. A patched xfdesktop4 package should show up in dapper-updates any time now.[/QUOTE]

Thank you. I tried that. It doesn't seem to change the desktop icon text nor the menu text.

---

### Post by Bad Seed on 2006-06-16
[quote=bbzidane]i fixed my right click menu problem
i just copied back the original menu into my local config directory and that fixed that

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```[/quote] Thanks a lot :D. I came here looking for the same issue and now I have again my right click menu \\:D/.

Cheers.

---

### Post by woot on 2006-06-21
joining the club of the happy-i've got my menu back- people :) Though the menu which I can access with the button is still gone, maybe some reset will resolve that

---

### Post by Krigsoffer on 2006-06-21
What exactly is the procedure for this operation?

I have the same problem, and would like some help.

---

### Post by woot on 2006-06-22
[QUOTE=Krigsoffer]What exactly is the procedure for this operation?

I have the same problem, and would like some help.[/QUOTE]


this should do the trick..it its what you're asking for

[QUOTE=bbzidane]i fixed my right click menu problem
i just copied back the original menu into my local config directory and that fixed that

```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```[/QUOTE]

---

### Post by Krigsoffer on 2006-06-22
Yeah, but am i supposed to run that in the terminal?

---

### Post by Bad Seed on 2006-06-22
[quote=Krigsoffer]Yeah, but am i supposed to run that in the terminal?[/quote] That's what I did and worked for me.

---

### Post by Krigsoffer on 2006-06-22
Nothing happened when trying to do it with the terminal...

But, I did it manually, and that worked, so everything is fine now.

But it is really annoying. Everytime i try to modify the menu, it dissapears... Isn't there any way to resolve this?

---

### Post by dmizer on 2006-06-24
this worked for me in breezy.  wish i knew how to get the bottom panel back, but at least i have the right click capability again.

thank you kindly.

edit ... restored lower xfce panel as well ...
right click > select "run program" > and type: xfce4-panel > click "run"

you now have a lower panel as well.

---

### Post by changlinn on 2006-06-26
I tried cp'ing the menu file, it didn't give me the right click back, still no good

---

### Post by changlinn on 2006-06-27
found out xffm-deskview was the culprit, just killed that and started xfdesktop and all was back as normal.

---

### Post by dylanv on 2006-08-03
I had the missing xfce menu (top left), and that fixed it. Thanks!

---

### Post by tandre75 on 2006-08-08
...
edit ... restored lower xfce panel as well ...
right click > select "run program" > and type: xfce4-panel > click "run"
...


The above suggestion gave me back both the top and bottom panels.

Thanks a lot
:D

---

### Post by kljaver on 2006-08-10
> **bbzidane said:**
> just want to say the exact same thing happened to me
right click on desktop stopped doing anything
and my menu is empty

hope someone can provide a solution to this

More simple way: just delete ~/.config/xfce4/desktop/menu.xml and relogin

---

### Post by Wangsta on 2006-10-04
> **psychicdragon said:**
> The default font is 'Sans 9'.


 i have the same problem.

i changed the titles on the top of the windows back, but how do you change the other text back; the text in synaptic, thunar, desktop stuff etc.?

---

