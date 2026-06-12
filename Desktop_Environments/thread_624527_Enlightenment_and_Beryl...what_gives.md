---
title: "Enlightenment and Beryl...what gives?"
date: 2007-11-27
forum: Desktop Environments
---

### Post by teddybairs1 on 2007-11-27
I've been playing around with enlightenment dr17 lately and found that I enjoy it in spite of it's differences and the occasional bug I've found. But one thing I'm trying to understand is why when I try to switch the window manager to beryl that it logs me out of the desktop. Beryl runs fine under KDE and Gnome, so why not Enlightenment. Any ideas or fixes? Anyone?

---

### Post by eXisor on 2007-11-27
You are confusing a WM with a DE.

Check this thread [http://forum.compiz-fusion.org/showthread.php?t=4317](http://forum.compiz-fusion.org/showthread.php?t=4317) for a better explanation, but basically e17 and beryl/compiz are window managers, whilst KDE and Gnome are DE's (desktop environments?).
.

---

### Post by teddybairs1 on 2007-11-27
I am well aware of the difference between a wm and a de. I am also aware that E17, in it's most literal sense, is a WM capable of being run under either gnome or KDE. This being said, I am using an E17 DE at the moment including all menus, shelves, gadgets, etc. It is not Gnome, and it is not KDE. It even has it's own display manager and startup called "entrance". For that matter E17 is the DE for the new gOS PCs from Everex.

My question was not why two WMs cannot coexist peacefully at the same time. I am not such a noob that I can't figure that one out. My question was why I can't switch between the E17 window manager and Beryl within the Enlightenment DR17 Desktop Environment. (And if you insist that E17 cannot be a Desktop Environment then I recommend you check out the Ubuntu Wiki on "Ebuntu" or "Elbuntu")

I am willing to accept that Enlightenment is a WM overlaid onto an X session. My question then becomes again, why can't it be swapped out for Beryl using the beryl-manager?

---

### Post by Anthem on 2007-12-08
Short version?  Because the enlightenment folks haven't ported Compiz to E17.

Compiz was originally a Gnome WM... it had to be hacked to run on KDE.  The Enlightenment guys are going an entirely different way... I don't know that Compiz/Beryl will ever run on E17.

---

### Post by marsmissionaries on 2007-12-09
That is basicly the same as asking why you can not run KWin and Metacity at the same time.

---

### Post by teddybairs1 on 2007-12-09
Anthem, thank you. That was more of a reply I was looking for. Why couldn't some of the other guys just say that instead of trying to insult my intelligence and put there own ignorance on display for all to see?

Marsmissionaries, please see my above response to the same kind of reply you gave. Also, I would recommend you do some research on elbuntu and geubuntu, two distros which have chosen to use the E-dr17 desktop environment as opposed to gnome or kde.

---

### Post by Forlong on 2007-12-10
> **Anthem said:**
> Compiz was originally a Gnome WM... it had to be hacked to run on KDE.
Not true, Compiz has always been a window manager that conforms the ICCCM and can therefore be used to replace any other window manager.
It is true that it's better *implemented* in GNOME than KDE but that's a totally different issue.


@teddybairs1: since you can't replace Enlightenment's window manager with *any other* wm (openbox, wmii, whatever...), you can't use Beryl/Compiz with it's "DE"

So in a way, the previous answers weren't ignorant at all (they just didn't answer the initial question).

---

### Post by teddybairs1 on 2007-12-11
Why can't you replace E17's wm? I've had metacity running under kde before. Is it just a limitation of the software?

---

### Post by kelvin spratt on 2007-12-11
As far as I know E17 does not use 3d effects to achieve its bling but gives superior 2d effects than other window managers and is very light on recourses.

---

### Post by sirdilznik on 2007-12-11
> **teddybairs1 said:**
> Why can't you replace E17's wm? I've had metacity running under kde before. Is it just a limitation of the software?

You can replace E17's WM, but then it's not E17 anymore.  E17 right now basically **is** the Window Manager.  Rather than have separate programs for many fo E17's tasks outside of it being a Window Manager, it generally uses modules which will only work with E17 running as the WM.  Thus if you take away th WM, say goodbye to the modules as well.  There are E17 separate programs too but many are incomplete so there really is nothing left of E17 once you replace the WM.

E17 is not compiz, it will never be compiz, it was never intended to be compiz or work with compiz.  E17 will eventually have it's own awesome effects, but Raster is waiting for Xorg technology to catch up (namely XRender...  /shakes fist at XFree86 ) so that it can be done properly and not with a hack like xcompmgr.  As it is you can do real transparency and shadows with xcompmgr running on top of E17 now or by using the "bling" module (though it was unstable last time I tried) and the effects are very basic (transparency, drop shadows, fade in/out).

---

### Post by Forlong on 2007-12-11
> **teddybairs1 said:**
> Is it just a limitation of the software?
Yes, it's not a real DE (hence the "") - at least you can't compare it to GNOME, KDE and Xfce.
sirdilznik's post has pretty much the answer.
But to keep it short: you can't replace Enlightenment's wm because the developer (Raster) doesn't want you to.
It could be possible but that would require a lot of duplicate effort.

I don't think Enlightenment will ever be a "real" DE. Xfce started out solely as a wm as well but Raster has no intention to take that direction.
He's a little quirky anyway. :)

---

