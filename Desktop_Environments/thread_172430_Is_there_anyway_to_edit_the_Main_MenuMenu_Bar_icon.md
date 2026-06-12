---
title: "Is there anyway to edit the Main Menu/Menu Bar icon?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by PrimoTurbo on 2006-05-08
I'm trying to customize my desktop, is there anyway to edit the Main Menu & Menu Bar icons.

I want to use the Main Menu option and basicly I want to remove the little black arrow because it doesn't look good and I want to edit the default Ubuntu logo and add something a little better like a 3d logo or something. Thanks :)

---

### Post by Omnios on 2006-05-08
It is possible there is a post on the forum about it but dont remember where lol.

---

### Post by PrimoTurbo on 2006-05-08
Do you remember any word in the title of that thread because I did a couple of searches before this post and didn't find anything.

---

### Post by Omnios on 2006-05-08
Forget because it was a couple months ago but it was about changing the Ubuntu Menu icon into the gnome foot.

---

### Post by Ramses de Norre on 2006-05-08
The image: ```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

---

### Post by PrimoTurbo on 2006-05-08
Thanks Ramses de Norre, but I'm also really hoping it's possible to remove the arrow? The graphic that I want to use overlaps it and it looks ugly. ](*,)

---

### Post by PrimoTurbo on 2006-05-08
[QUOTE=Omnios]Forget because it was a couple months ago but it was about changing the Ubuntu Menu icon into the gnome foot.[/QUOTE]

There is a spelling mistake in your sig :) Insatlling software, it's Installing. Any more ideas?

---

### Post by cmaxter on 2006-05-08
/*
if you want to change the gnome-foot logo next from the Applications menu into the Ubuntu logo this is all you have to do:
*/

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

/*
see here: [http://www.ubuntuforums.org/archive/index.php/t-26854.html](http://www.ubuntuforums.org/archive/index.php/t-26854.html)

the next reply at this post whas "it worked! Thanks!"

I'm thinking it can work any way you want it to, right?
*/

---

### Post by PrimoTurbo on 2006-05-09
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

Doesn't seem to work for the logo near Applications, but it does change Main Menu logo if you add it. The problem is that the Main Menu still has the lame \/ arrow, any ideas guys?

I tried sudo killall gnome-panel and even restarted didn't change the Applications logo. :(

---

### Post by Ur1el on 2007-07-25
What about removing the switch user icon from the sub menu? 
<--admitted neophyte, but I have searched around to remove this with no luck.
Thanks in advance.

---

