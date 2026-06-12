---
title: "Unity's Dash in other DE's"
date: 2012-09-21
forum: Desktop Environments
---

### Post by KellKheraptis on 2012-09-21
Has anyone ever attempted to put the dash in another DE?  I'd love to run that feature on say, Openbox.  Just curious, and also curious how feasible its implementation would be.  Thanks!

---

### Post by wojox on 2012-09-21
Openbox is a window manager. Compiz is a compositing window manager. I don't think it would work that way.

---

### Post by KellKheraptis on 2012-09-21
> **wojox said:**
> Openbox is a window manager. Compiz is a compositing window manager. I don't think it would work that way.

There's xcompmngr for that in OB.  I just want the Dash (Winkey bind to open the Unity Dash).

---

### Post by wojox on 2012-09-21
Right, unity is a plugin for compiz. That's what I was getting to.

---

### Post by KellKheraptis on 2012-09-21
> **wojox said:**
> Right, unity is a plugin for compiz. That's what I was getting to.

I see, and good to know.  If nothing else, it makes it a lot easier to look for the code, now :D  I do know you can run Compiz without a DE below, so there's gotta be a way to poach its plugins.  Thanks for the heads up!  Also, has anyone ever tried to port plugins in this manner?  I'll ask here, but also going to check around the WM section some more for it.

---

### Post by wojox on 2012-09-21
Here's the code for [Unity]("http://askubuntu.com/a/28472/2973")

---

### Post by KellKheraptis on 2012-09-21
> **wojox said:**
> Here's the code for [Unity]("http://askubuntu.com/a/28472/2973")

Thanks wojox.  I actually snooped around the forum and was lead to the Gnome extensions, which I am pretty sure I can get to work in Openbox (since I'll be using gnome's panel for the Cinnamon app menu, so no extra deps).  It got me pointed in the right direction.  I still might try and turn it into a standalone if I'm really feeling froggy this weekend :D

---

### Post by zombifier25 on 2012-09-22
You can also run the Unity 2D Launcher (which is independent from Compiz) along with the Dash in Openbox. Theoretically it should work, can't see any reason it shouldn't. Run ```
unity-2d-shell
```

---

### Post by KellKheraptis on 2012-09-23
> **zombifier25 said:**
> You can also run the Unity 2D Launcher (which is independent from Compiz) along with the Dash in Openbox. Theoretically it should work, can't see any reason it shouldn't. Run ```
unity-2d-shell
```

You know, I hadn't thought of that...does 2D still use Metacity btw?

---

### Post by zombifier25 on 2012-09-25
> **KellKheraptis said:**
> You know, I hadn't thought of that...does 2D still use Metacity btw?

Yes.

---

