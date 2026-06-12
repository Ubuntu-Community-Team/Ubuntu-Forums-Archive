---
title: "Opacity for all windows set to 0."
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by Islington on 2007-12-26
SO I was messing around with ccsm and accidentally set all my window opacity to 0.
How can I log into gnome without starting Compiz? (so I can fix the Opacity)
Is there a command to get me into the sessions option from the failsafe terminal?

If nothing works I will uninstall compiz, but I would rather not do that.

---

### Post by chewearn on 2007-12-26
> **Islington said:**
> SO I was messing around with ccsm and accidentally set all my window opacity to 0.
How can I log into gnome without starting Compiz? (so I can fix the Opacity)
Is there a command to get me into the sessions option from the failsafe terminal?

If nothing works I will uninstall compiz, but I would rather not do that.

Maybe you can try this:
Log-in gnome first, then press CTRL+ALT+F1 to go to console.  Log-in the console, then:
```
metacity --replace
```
That should stop compiz, so you can switch back to gnome (CTRL+ALT+F7) to fix things.

---

### Post by Islington on 2007-12-26
> **AstalaVista said:**
> Maybe you can try this:
Log-in gnome first, then press CTRL+ALT+F1 to go to console.  Log-in the console, then:
```
metacity --replace
```
That should stop compiz, so you can switch back to gnome (CTRL+ALT+F7) to fix things.

thankyou for the fast response, however disaster was avoided.

my filter in the general options was this:
```
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```
but for some strange reason I was still able the access the gnome appearance menu item, without opacity interfering. From there I was able to fix it.

Why did the appearance window not follow the opacity rule?

---

### Post by Forlong on 2007-12-26
You can't run metacity from the console, since it's a graphical application.
This would do the job:
```
DISPLAY=:0 metacity --replace
```


But what's certainly easier is logging into the failsafe Gnome session in GDM and start ccsm from there to undo whatever you did.

---

### Post by Forlong on 2007-12-26
> **Islington said:**
> Why did the appearance window not follow the opacity rule?
Because it's of the type **Dialog** (not Normal, Utility or Unknown)

---

### Post by Islington on 2007-12-26
> **Forlong said:**
> You can't run metacity from the console, since it's a graphical application.
This would do the job:
```
DISPLAY=:0 metacity --replace
```


But what's certainly easier is logging into the failsafe Gnome session in GDM and start ccsm from there to undo whatever you did.

I tried doing the easy method and it was no go. failsafe gnome loaded up compiz. Thanks for the command though, it might prove useful, if anyone else does the same thing.

---

### Post by Forlong on 2007-12-26
> **Islington said:**
> I tried doing the easy method and it was no go. failsafe gnome loaded up compiz.
How did you install Compiz? This should definitely work with Gutsy - and therefore backported packages for Feisty as well.

---

### Post by Islington on 2007-12-26
it was the default compiz that came with gutsy. let me try it out again just to be sure.

Edit: nevermind, it works.

---

