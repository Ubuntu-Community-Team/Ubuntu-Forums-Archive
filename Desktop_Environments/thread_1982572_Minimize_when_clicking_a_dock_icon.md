---
title: "Minimize when clicking a dock icon"
date: 2012-05-18
forum: Desktop Environments
---

### Post by Cardale on 2012-05-18
I am very confused why when you click an icon on the dock you can unminimize it, but can't minimize it.

Can some one explain the logic of this to me?

---

### Post by na5h on 2012-05-18
Well, um...I don't really know what to say about this...but if you have multiple windows open for the same application, clicking on the dock icon will zoom out of the desktop and allow you to conveniently switch between them. So...I suppose the dock icon is more of a "show all open windows and allow me to switch between them" button rather than a "minimize to system tray" button?

I've never really come to think of it as inconvenient or odd...I just switch between applications by clicking on their respective icons. If I want to minimize a window I simply move my cursor to the top left corner of it...most of the time there's no need for that, though...

---

### Post by grahammechanical on 2012-05-18
Each application comes with its own Close, Minimum, Maximum icons to do that. Enough people complained when they were switched from right to left in the applications top panel. Now they go into the top panel on the left when the application is maximized.

You can maximize an application by dragging its top panel up to the desktop's top panel. You can restore it by clicking the desktop's top panel.

What if someone chooses to have the launcher set to autohide. It means that they have to reveal the launcher to minimize it. What you expect to be default behaviour is in fact redundancy.

Regards.

---

### Post by nevle on 2012-05-18
When i minimize the app disappears, a small arrow appears near my icon but thats it, the computers freezes or takes a minute to reopen when i click on it. Cant see if i have more than 1 window open, what can i do?
ps doesn't zoom out, just sits there..

---

### Post by na5h on 2012-05-18
> **nevle said:**
> When i minimize the app disappears, a small arrow appears near my icon but thats it, the computers freezes or takes a minute to reopen when i click on it. Cant see if i have more than 1 window open, what can i do?
ps doesn't zoom out, just sits there..

Well, if nothing happens than I suppose you only have one windows of that application open? You can try it out by opening your home folder and hitting CTRL+N to open another window. Clicking on the home folder icon should then show you the two windows side by side. Alternatively, you can click on the "workspaces" icon (SUPER+S) to get a view of all your open windows on all four desktops.

---

### Post by Cardale on 2012-05-19
Appreciate the comments.

Currently if you use the Unity dock and have a application maximized and go to click on the toolbar icon for that application it does absolutely nothing.

In my humble opinion this is not the expected behavior.

All docks from Docky, AWN, Gnome, KDE, Windows have this functionality.

I think Mac does nothing as well.

Unity has just nothing.

That click event could easily be hooked to optional functions for that event.  For instance if when you click the icon you want to do minimize then it will do it, or some other useful idea.

---

### Post by Frogs Hair on 2012-05-19
> You can maximize an application by dragging its top panel up to the  desktop's top panel. You can restore it by clicking the desktop's top  panel.

What if someone chooses to have the launcher set to autohide. It means  that they have to reveal the launcher to minimize it. What you expect to  be default behaviour is in fact redundancy.


Agreed , Docky wasn't chosen as the basis of Unity because of its limitations . I was a dock user prior to unity and no longer  see the need , but to each their own . Running Classic  with a dock may be a more usable option for you.

---

### Post by Cardale on 2012-05-19
So the verdict by the majority of posters is that after a maximized application is displayed that icon should do nothing?

---

### Post by markbl on 2012-05-20
> **Cardale said:**
> So the verdict by the majority of posters is that after a maximized application is displayed that icon should do nothing?
But it does do "something". It shows a scale view of all open windows of that same app. If there are no other open windows then it implicitly tells you because it does not enter scale view.

I can see the reasoning that minimisation is an orthogonal function to scale view so should not be overloaded into the second click of a launcher icon. Really, minimisation is not really needed with these modern desktops. I have weaned myself off the urge to minimise. Gotta move forward with the times.

---

### Post by mc4man on 2012-05-20
Logic doesn't really come into play here, there is some techo-babble that supports how it currently is.
As far as "verdict by the majority of posters" that also isn't really relevant.

On the other hand users/community can do as they please so here is a ppa that provides the left click minimize on unity launcher icons for 12.04 & 11.10, works ok when I tested it previously 

[https://launchpad.net/~ojno/+archive/unity-minimize-on-click](https://launchpad.net/~ojno/+archive/unity-minimize-on-click)

And there is this ppa that adds the above ppa's min action & returns the dodge window option, for 12.04 only
[https://launchpad.net/~ikarosdev/+archive/unity-revamped](https://launchpad.net/~ikarosdev/+archive/unity-revamped)
(haven't tried this ppa yet so can't comment on how it works out

---

### Post by Baldrick_NZ on 2012-05-20
> **mc4man said:**
> 
And there is this ppa that adds the above ppa's min action & returns the dodge window option, for 12.04 only
[https://launchpad.net/~ikarosdev/+archive/unity-revamped](https://launchpad.net/~ikarosdev/+archive/unity-revamped)
(haven't tried this ppa yet so can't comment on how it works out

I've tried this PPA, and it's well worth the effort!

It does exactly as mc4man says, returns the dodge effect and minimise on-click.

I, for one, am very happy with it!

I believe the ppa is a fork of unity (of sorts), so it's not offically supported by Canonical - use at your own risk stuff - but then what third-party apps aren't?

---

### Post by wilee-nilee on 2012-05-20
The cairo-dock does this and more check it out.

---

### Post by mc4man on 2012-05-20
I was just going to edit my post but see a new comment - 
anyway the J.french ppa for min on left click only works when a single app window is open. If there are 2 or more then it only goes to spread.
Not sure why he hasn't fixed

The unity-revamped ppa has fixed J. French's patch to allow multiple windows so likely that is the one to use.

Myself don't use Dodge on this laptop, the screen is small, (13") so I tend to keep the launcher exposed at all times.

Also I've grown tired of waiting for the custom color settings to be fixed so here I've taken the French patch, added the multi window fix, patched to fix custom colors & re-built

I guess the point is many times you can get what you want, (not always)

---

### Post by mc4man on 2012-05-20
> **wilee-nilee said:**
> The cairo-dock does this and more check it out.
Does the cairo-dock have something like quicklists? ( & DnD based on MimeType

at least here I can take care of about 35 things thru 4 icons, don't really want 35 icons, Do find DnD very useful

---

### Post by wilee-nilee on 2012-05-20
> **mc4man said:**
> Does the cairo-dock have something like quicklists?
(- at least here I can take care of about 35 things thru 4 icons, don't really want 35 icons

Cairo has a full menu list as well as stuff that can be added and removed, it has a stack folder that you can pile in whatever you want I have some stuff in there like code  lists etc, music player prompt.

It is a easy install and purge I would try it out and see if it works for you.

---

### Post by mc4man on 2012-05-20
> It is a easy install and purge I would try it out and see if it works for you.
I'm always up for trying things so will ck. it out (did use for a while in gutsy or there-abouts

---

### Post by wilee-nilee on 2012-05-20
> **mc4man said:**
> I'm always up for trying things so will ck. it out (did use for a while in gutsy or there-abouts

I have only used it in the last 6 months so I suspect it is a bit different now, have fun. ;)

---

