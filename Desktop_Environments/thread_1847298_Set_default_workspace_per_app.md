---
title: "Set default workspace per app?"
date: 2011-09-20
forum: Desktop Environments
---

### Post by Naatan on 2011-09-20
Hi, just wondering if it's possible to have Ubuntu remember what workspace an app was in. Right now if I logout and log back in all apps just launch in the current workspace, rather than the one they were in last time.

Is it possible? (without messing in config files).

---

### Post by Elfy on 2011-09-20
If you're using compiz there's a plugin that will do that - workspace rules - from memory.

You can use devilspie to achieve the same - if not using compiz.

Not sure you can do it without changing anything though.

---

### Post by Krytarik on 2011-09-20
> **forestpiskie said:**
> If you're using compiz there's a plugin that will do that - workspace rules - from memory.
The actual name is "Place Windows", you will find it in "CompizConfig Settings Manager -> Window Management". Obviously, you need CCSM to be installed, package "compizconfig-settings-manager".

In the plugin's settings, under "Fixed Window Placement -> Windows with fixed viewport", create a rule, and "Grab" the "Window Class" via the "+"-icon beneath the field "Viewport positioned windows", then set the "Viewport Position" depending on your workspaces setup.

Greetings.

---

### Post by kohoutek1 on 2011-10-05
"Place Windows" not working for me.

What value should be set on "X" and "Y" viewport positions, if, for example, my horizontal desktop size is "4", vertical is "1", and I want Firefox to always open on viewport 1? Is it "1" and "1"? 

And will "window class=Firefox" be correct?

---

### Post by Krytarik on 2011-10-05
> **kohoutek1 said:**
> What value should be set on "X" and "Y" viewport positions, if, for example, my horizontal desktop size is "4", vertical is "1", and I want Firefox to always open on viewport 1? Is it "1" and "1"?
Exactly, which is the most left one.

> **kohoutek1 said:**
> And will "window class=Firefox" be correct?
Nope, actually, it's just:
```
class=Firefox
```

---

### Post by kohoutek1 on 2011-10-09
"Place Windows" looks like a better bet than Devil's Pie for getting apps assigned to specific workspaces, but it's still not working for me.

Are there other settings in CCSM that might be conflicting?

---

### Post by Krytarik on 2011-10-09
Are you even running Compiz!?
Do you get any of its effects?

What version of Ubuntu are you running?
If Natty or Oneiric, are you using classic Gnome or Unity?

Is the "Place Windows" plugin even enabled?

Btw., Devil's Pie is for Metacity.

---

### Post by kohoutek1 on 2011-10-10
> **Krytarik said:**
> Are you even running Compiz!?
Do you get any of its effects?

What version of Ubuntu are you running?
If Natty or Oneiric, are you using classic Gnome or Unity?

Is the "Place Windows" plugin even enabled?

Btw., Devil's Pie is for Metacity.

Running Natty. Classic Gnome.

Place Windows plugin is enabled, and I get all other desired CC effects.

Devil's Pie now has a command for CCSM, which is set_viewport, but that didn't work. Then someone in this thread led me toward the right CC plugin, and here we are;)

I disabled DP, made sure the daemon wasn't starting at log in. Still no go.

Must be something basic I'm missing, but I can't yet think of what that might be...

---

### Post by kohoutek1 on 2011-10-10
OK, got it... 

On a hunch, I enabled the "window rules" plugin, and ahah!

So, for those who have the same question:

Enable "Window Rules", then "Place Windows," then follow the steps Krytarik outlined.

---

### Post by kohoutek1 on 2011-10-12
What about then having the viewport switch to the viewport where the application has just been opened?

---

### Post by Krytarik on 2011-10-12
> **kohoutek1 said:**
> What about then having the viewport switch to the viewport where the application has just been opened?
Nah, that isn't possible, at least not without tinkering with the app's startup command, involving "wmctrl". I really think that it isn't worth the hassle. ;)

Btw., it's really strange if "Place Windows" depends on "Window Rules" in your case, as they have no obvious connection. At my system, Lucid 10.04, that isn't the case, I just tested that.

---

