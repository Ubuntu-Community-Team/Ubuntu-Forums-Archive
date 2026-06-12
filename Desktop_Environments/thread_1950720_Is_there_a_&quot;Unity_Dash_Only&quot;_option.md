---
title: "Is there a &quot;Unity Dash Only&quot; option?"
date: 2012-04-01
forum: Desktop Environments
---

### Post by Aielyn on 2012-04-01
I've got an idea for how I'd like my Ubuntu set up. To me, Unity itself just isn't right - I don't like it.

The one thing I *do* like about Unity, though, is the Dash itself. Now, there is a new pane I'd like to see for it, but that's an issue for another day.

What I'm wondering is, is there a way to get *only* the Dash itself, and not, for instance, the Launcher? Whether it's through Unity 2D, a mod, or something else, I don't mind, so long as it's the same Dash as Unity uses.

What I'm thinking is that I'd like to remove both the launcher and the top panel. I already use Avant Window Navigator, and like it. Beyond that, I just need some sort of indicator dock, and I can figure that one out from a variety of options (I saw one method of making something similar using an avant mod).

Essentially, I'd like to be able to simply roll my mouse over the top-left corner of the screen, and have the dash come out, fully active, without the launcher (which would just be taking up space). But if I can't get the roll-over approach, then at least I'd like to be able to do a similar thing by pressing the Super button (which already summons the dash, but with the launcher).

It's all about the interface itself - my system is fast enough to run any of the regular environments, so if it's full-fledged Unity, but with the launcher deactivated, I'm fine with that.

So, in case my rambling meant you missed the question: Is there a way to reduce Unity to just the Dash itself, and not the top panel or launcher, or load only the Dash in another environment?

---

### Post by zombifier25 on 2012-04-01
Yeah... I'm curious about this too. I know that GNOME Do or Synapse may be able to replicate this, however its functionality is too limited, and they only search exact text (like if your system is using a locale different than English, then you can't search in English)
Meanwhile, you can hack ccsm and set the Unity launcher to never show up :P The panel, I dunno.

---

### Post by Frogs Hair on 2012-04-01
You could open the synaptic package manager and look at all the dependencies to see what packages are required for dash . If it is tied to the launcher you may be out of luck for now .

---

### Post by Aielyn on 2012-04-02
> **Frogs Hair said:**
> You could open the synaptic package manager and look at all the dependencies to see what packages are required for dash . If it is tied to the launcher you may be out of luck for now .

As far as I can tell, there's no package for Dash only, just unity-2d-launcher. I assume that the dash is part of that package (and that the 3d version is all within the unity package itself).

---

### Post by zombifier25 on 2012-04-03
hmm in 12.04 the unity-2d-launcher is merely a dummy package.
So we're out of luck.

---

### Post by Aielyn on 2012-04-06
I may have found something that will work as an alternative to unity, for the time being, in the way that I want this to work.

The people behind elementary OS have made a launcher called slingshot (which is apparently modelled on certain other launchers on other OSes). While not nearly as clean and pretty as Unity's dash, and while lacking the extra 'lenses', it has the one lens that I wish Unity had: an application menu lens (think of the old gnome menu system, but in lens form).

It's available via ppa, and it can be set, with compiz, to run when you put the cursor in the top-left corner (using the "Commands" settings under General). You have to click somewhere to remove it (rather than going back into the corner), and the version for 11.10 doesn't frost the transparency, so there's some background-bleed issues, and it takes a moment to come up (rather than being instant) in 11.10, but it does open up the possibility of trying out my idea for my ideal desktop. (EDIT: I just tried using the elementaryOS's main ppa, and it has a newer version of slingshot in it - while it looks a bit odd with the little arrow pointing up at the ordinary Unity panel in my testing, and will look even stranger without any panel, it is a step closer - you can return to the corner to hide the program again, it does frost the transparency effect, and it feels just a little more natural, visually... still nowhere near Unity's Dash, though, and requires more clicks than I'd like)

I still want a Unity-Dash-Only setup, though.

---

### Post by Aielyn on 2012-04-10
Looks like someone is actually working on a launcher mimicking the Unity Dash, for Gnome Shell.

[http://www.omgubuntu.co.uk/2012/04/new-extension-brings-unity-dash-to-gnome-shell/](http://www.omgubuntu.co.uk/2012/04/new-extension-brings-unity-dash-to-gnome-shell/)

Here's hoping that I can get it set up to work the way I want it when it releases, because this is exactly what I want in terms of style.

---

### Post by Frogs Hair on 2012-04-10
> **Aielyn said:**
> Looks like someone is actually working on a launcher mimicking the Unity Dash, for Gnome Shell.

[http://www.omgubuntu.co.uk/2012/04/new-extension-brings-unity-dash-to-gnome-shell/](http://www.omgubuntu.co.uk/2012/04/new-extension-brings-unity-dash-to-gnome-shell/)

Here's hoping that I can get it set up to work the way I want it when it releases, because this is exactly what I want in terms of style.

I found this on the 12.04 thread . [http://ubuntuforums.org/showthread.php?t=1955927](http://ubuntuforums.org/showthread.php?t=1955927)

---

