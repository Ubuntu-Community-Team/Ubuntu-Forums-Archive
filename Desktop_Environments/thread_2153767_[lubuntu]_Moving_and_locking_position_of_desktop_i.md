---
title: "[lubuntu] Moving and locking position of desktop icons"
date: 2013-06-12
forum: Desktop Environments
---

### Post by lonewolfLINUX on 2013-06-12
Hi everybody!

I've installed Lubuntu 13.04 (LXDE) on a laptop ASUS [A6VA-Q021H]("http://notebookitalia.it/review-asus-a6va-q021h.html") with just one user, only me. That is normal installation.

Everything works fine, except one: 
[B]I would like to move and lock the position of my desktop icons wherever I want, 
but everytime I do it with restart/logout/switch-user the all automatic align to the left of the screen![/B]

I tried all the combinations of ***Stick to current position*** and ***Snap to grid*** options (visible on right-click menu)
and also I tried to move them one by one or in group, but with next restart/logout/switch-user they are auto-aligned again on the left.


Suggestions? Solutions? There is a kind of system file for icons positions in LXDE?

Thank you!

---

### Post by toxicbreakfast on 2013-06-12
Well, the system file is at ~/.config/pcmanfm/lubuntu/desktop-items-0.conf

```

[foo.desktop]
x=100
y=100

[bar.desktop]
x=200
y=200

```

etc.

---

### Post by IbsUser on 2013-06-12
> **toxicbreakfast said:**
> Well, the system file is at ~/.config/pcmanfm/lubuntu/desktop-items-0.conf

```

[foo.desktop]
x=100
y=100

[bar.desktop]
x=200
y=200

```

etc.
Hi,

Comment #2 is correct. But I believe it's not necessary to change that file whenever you need to move icons. 

In order to replicate, I did the same you did at comment #1 and it worked for me on my Lubuntu 13.04 32 bits. However, yes, sometimes after shutdown/reboot some of my icons changed place a little.

A friend at LXDE forum feels the same:
[http://forum.lxde.org/viewtopic.php?f=22&t=36341&p=48376&hilit=desktop+icons#p48378](http://forum.lxde.org/viewtopic.php?f=22&t=36341&p=48376&hilit=desktop+icons#p48378)

Would that be a bug on PCManFM?

Cheers!

---

### Post by lonewolfLINUX on 2013-06-13
Thank for the answer, I studied that file and I discovered [that]("http://sourceforge.net/tracker/?func=detail&aid=3094187&group_id=156956&atid=801864") "bug":

> [I][FONT=arial]desktop-items-0.conf isn't writing changes when "Stick to Current Position" is unchecked.[/FONT]
[FONT=arial]The file is changed (updated) only when some icon is moved to a sticky position. If files are unsticked, no changes are made to desktop-items-0.conf[/FONT]

[/I][FONT=arial]*Expected behaviour would be to delete the information for the icon in desktop-items-0.conf when uchecking "Stick to Current Position".*[/FONT][COLOR=#555555][FONT=arial]

[/FONT][/COLOR]It is dated 2010!

And my problem persists... that is, I observed that **desktop-items-0.conf **just maintains the positions of icons of the last time I moved them and I clicked on ***Stick to current position*** and ***Snap to grid***.
When I reboot the icons are again on the left side and **desktop-items-0.conf** contains the correct positions I set before.

---

### Post by lonewolfLINUX on 2013-06-13
Another strange effect is the following.
 
When I reboot all icons are automatically realigned on the left side
and if I right click on every single icon, the option ***Stick to current position*** is unchecked.

If I drag and drop one of these icons somewhere on the desktop 
and then I right click on it, now ***Stick to current position*** is checked! Also if I didn't checked it!

**And if uncheck it the icon automatically moves and realigns itself on the left side!**

---

### Post by lonewolfLINUX on 2013-06-13
I didn't resolve anything, anyway I report that I changed the permissions of the file running:
```
chmod 777 [COLOR=#000000]*~/.config/pcmanfm/lubuntu/desktop-items-0.conf*[/COLOR]
```

Then I deleted all the content of the file, I saved and closed it. 
I dragged and dropped some of my icons on the desktop, than I reopened [COLOR=#000000]*desktop-items-0.conf *[/COLOR](before it was empty) 
and now it contained the coordinates of the icons I moved.

I set the *immutabiliy* to that file with:
```
sudo chattr +i [COLOR=#000000]*~/.config/pcmanfm/lubuntu/desktop-items-0.conf*[/COLOR]
```

I rebooted and icons were all again on the left side, automatically realigned...
I reopened [COLOR=#000000]*desktop-items-0.conf *[/COLOR]and it still contained the coordinates of the icons I moved before.

If anyone knows something please let me know!

---

### Post by Dreamer Fithp Apprentice on 2013-09-16
Bumping this because I also seek to lock them in place after I put them where I want them. Or at least change the way the autoarranging is done so I can keep the upper left corner area vacant.

---

