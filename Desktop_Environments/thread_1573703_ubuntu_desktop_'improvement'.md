---
title: "ubuntu desktop 'improvement'"
date: 2010-09-13
forum: Desktop Environments
---

### Post by lifebarier on 2010-09-13
hello.
need hellp at making my ubuntu more awesome :D
1. how to prevent icons on desktop? Windows has "don't show desktop icons" where/how can I get it on Ubuntu?
2. Terminal integrated to desktop. Console on desktop with lets say some border or so, but its carved into walpaper.
3. system resource monitor. will try to use conky so you can ignore this one for now, but know how unlucky last time was.... (clicking and dragging on conky made selection area teleport...)
4. Add email reading to my desktop with control buttons (or controlled via terminal)

I am quite green about linux so if you can help please write as clear as you can, if you can't... I'll have to use my brain.

oh and yes I am trying to make something like "digital hazard"

---

### Post by sdowney717 on 2010-09-13
have you looked at guake for the terminal idea?
[http://guake.org/screenshots](http://guake.org/screenshots)

---

### Post by lifebarier on 2010-09-13
I should check out that guake. But I don't think it will be what I need (at least judging from screenshots )

---

### Post by Noz3001 on 2010-09-13
Install a tiling window manager, like Awesome

---

### Post by cariboo on 2010-09-13
Moved to Desktop Environments, you'll probably get better answers here, that in the Cafe.

---

### Post by hrickh on 2010-09-13
> **lifebarier said:**
> hello.
need hellp at making my ubuntu more awesome :D
1. how to prevent icons on desktop? Windows has "don't show desktop icons" where/how can I get it on Ubuntu?
2. Terminal integrated to desktop. Console on desktop with lets say some border or so, but its carved into walpaper.
3. system resource monitor. will try to use conky so you can ignore this one for now, but know how unlucky last time was.... (clicking and dragging on conky made selection area teleport...)
4. Add email reading to my desktop with control buttons (or controlled via terminal)

I am quite green about linux so if you can help please write as clear as you can, if you can't... I'll have to use my brain.

oh and yes I am trying to make something like "digital hazard"

For number 1. - Run gconf-editor, apps/nautilus/desktop. Untick "volumes_visible".
For number 2. - Been asked a million times (including here on Ubuntuformums), but look here: [http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21](http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21)
For number 3. Conky's great.
For number 4. I'm not sure I understand what you mean.

R.
==

---

### Post by mannequin on 2010-09-13
For #3, I've always loved [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html").  May not be what you're looking for, though, on second read of your post...

HTH,
-M.

---

### Post by lifebarier on 2010-09-13
> **hrickh said:**
> 
For number 4. I'm not sure I understand what you mean.

R.
==


I mean that I want email reading tool that is carved in desktop. But on the other hand I could just do that with second terminal integrated to dektop + some terminal based email client. Just one problem - how to make such terminal be locked to only one application?

for  [http://maketecheasier.com/terminal-a...ntu/2008/05/21]("http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21") will it be movable? if yes any way to lock it in place? Sorry I can't test it right away.


> **Noz3001 said:**
> Install a tiling window manager, like Awesome

hell that thing looks interesting ^^ . only problem is I will need to do some more serious programing (no I am not a programmer... just studying it) and stuff so that thing would be not a best thing but I must try that.

EDIT: just checked Awesome installation.... I would ruin all my system doing that... and I guess I won't be able to switch back to gnome :D

EDIT2: just installed it. Very interesting

---

### Post by 3Miro on 2010-09-13
For number 1, it sounds like what you get from:

1. Alt + F2 and then run gconf-editor.
2. Then go to apps -> nautilus -> preferences and then remove "show desktop". This will probably also remove the wallpaper.

If you are running compiz (i.e. effects are on normal or higher), then you can install "Compiz Config Settings Manager" from Ubuntu software center.

Inside CCSM select to enable Wallpaper effects and then select the images that you want to use as wallpapers.

---

### Post by kerry_s on 2010-09-13
i agree with Noz3001, a tiling wm, terminal & terminal programs is exactly what that screenshot looks like.

if you want to play with something similar in gnome, have a look at bluetile->
[http://www.webupd8.org/2009/12/how-to-install-bluetile-in-ubuntu.html](http://www.webupd8.org/2009/12/how-to-install-bluetile-in-ubuntu.html)

---

