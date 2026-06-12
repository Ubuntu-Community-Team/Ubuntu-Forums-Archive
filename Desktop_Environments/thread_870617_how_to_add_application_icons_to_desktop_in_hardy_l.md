---
title: "how to add application icons to desktop in hardy lxde?"
date: 2008-07-26
forum: Desktop Environments
---

### Post by jittopjose on 2008-07-26
hello friends,
i tried to add applications from menu to the desktop by right clicking. but nothing happened. anybody know how to do this.
thanks,
jittos....

---

### Post by swisscow on 2008-07-26
Try dragging the icon from the menu to the desktop - worked for me

EDIT: Sorry, didn't read that you were using lxde, don't know if this will work (does in gnome)

---

### Post by jittopjose on 2008-07-26
thanks friend,
let me try.

---

### Post by PCMan on 2008-07-26
> **jittopjose said:**
> thanks friend,
let me try.

Look for your app shortcuts in /usr/share/applications.
Drag and drop them on the desktop.
Drag & Drop from menu is not supported yet.

---

### Post by jittopjose on 2008-07-27
drag and drop from application folder didnt work. it showed permission denied. instead i copied the icon to the desktop. now its worked.
thanks friend.

---

### Post by sengines on 2008-07-27
What about the taskbar section, how do you get icons to show in the taskbar window list, I only get one icon for everything. The only place I found info on this was at archlinux.org, I'm running ubuntu hardy.



I searched google and found a few "lxpanel icon rendering issues" pages but nothing on how to fix on ubuntu.

Thanks

---

### Post by sengines on 2008-07-28
I just love answering my own questions.
[https://sourceforge.net/tracker/index.php?func=detail&aid=2019094&group_id=180858&atid=894869](https://sourceforge.net/tracker/index.php?func=detail&aid=2019094&group_id=180858&atid=894869)

[http://hatred.homelinux.net/wiki/_media/zhurnal:2008-07-25_00.39_fiks_otobrazhenija_ikonok_prilozhenij_v_lxpanel:taskbar_complex.diff](http://hatred.homelinux.net/wiki/_media/zhurnal:2008-07-25_00.39_fiks_otobrazhenija_ikonok_prilozhenij_v_lxpanel:taskbar_complex.diff)

Pop the fix in here lxpanel/src/plugins

and change directories unless you want to search for it

cat file.diff | patch -p0

---

### Post by GhostAir89 on 2008-07-30
> **jittopjose said:**
> hello friends,
i tried to add applications from menu to the desktop by right clicking. but nothing happened. anybody know how to do this.
thanks,
jittos....

I had the same problem, I was toying with the lxpanel of LXDE
This is so simple
Right-click on the Lxpanel(taskbar) of LXDE
select Add/remove panel items
there click add button
now find Application launch bar
select it and click add
notice it is the last one (u can move it with the arrows at the right side)
u can close it now!
find your app launcher in your lxpanel
right-click -> app launcher bar settings
and just add whatever app you want

I hope yhis is helpful!
______________________
[IMG]http://i266.photobucket.com/albums/ii267/amy_spooky/Cute%20pics/icon%20graphics/help.gif[/IMG][IMG]http://i33.photobucket.com/albums/d90/crycon69/help.gif[/IMG]
Help to get help

---

