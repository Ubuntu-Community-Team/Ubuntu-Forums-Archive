---
title: "Strange Xgl/Compiz problems"
date: 2006-09-15
forum: Desktop Environments
---

### Post by CyberCod on 2006-09-15
Well, I've got it running, so I know I shouldn't complain, but I'm having a few erroneous quirks that I was hoping someone could help me with.



For starters, upon logging into gnome, the ubuntu splash-bar thing stays up there for about a full minute.  Its not on the other desktops, just the side of the cube that is facing forward at startup.

Not real big problem, but annoying.

2nd, it seems like Compiz Settings Manager doesn't keep the changes I make.  Is there some text file somewhere that I can edit to get the effects settings I want?

Seems like some of CSM works, but not other parts, and moreover, changes made do not last through a reboot.

Next problem is that the gnome panel and drawers act very strangely.  Windows go fullscreen sometimes up and behind the panel, (which effectively hides the top of the application)

The drawers keep overlapping themselves and their "Open" icon.


Any help would be greatly appreciated.  Thanx in advace.

---

### Post by jh0 on 2006-09-15
Could you provide a few more details? Specifically:
 - video card and driver name
 - what guide you followed to set it up

Did you create your own start script (compiz-start or similarly named) and place it in Preferences -> Sessions? If so, try replacing it with the new compiz-manager systray application, which is available in the latest Quinn repositories (beerorkid.com, etc.).

Be sure to upgrade every two or three days -- updates are released almost daily.

compiz.net has an excellent support forum as well.

---

### Post by CyberCod on 2006-09-15
My apologies, 

I am using nVidia TI4200 AGP graphics card.

I used the following guide at
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

---

### Post by ayoli on 2006-09-15
1) the gnome splash screen that stay a while is not compiz related problem, it used to happen to me with metacity, just clik on it will make it go.
2) csm settings are stored in ~/.compiz, you may set permissions on it like this (if not already done)
```
chmod -R 0755 ~/.compiz
```
3) i don't have problem with panel when maximized, and don't use drawers

---

### Post by CyberCod on 2006-09-30
Well, the problems were a result of multiple xgl install attempts conflicting with eachother.

I got it hammered out now.

The problem with this is that by the time one gets it working, one doesn't know which methods or instructions really did the trick.

](*,)

---

