---
title: "Windows starting under menu bar."
date: 2011-10-28
forum: Desktop Environments
---

### Post by Carllacan on 2011-10-28
Hi!

I've just upgraded to Ocelot and I'm having this little problem with my windows; when I open a new one it appears with his upper bar under my menu bar, so I have to drag it a few pixels down in order to see it completely.

Is this a generalized problem with Unity or I'm doing something wrong? I may have touched some things on the Compiz configuration...

Thanks!

---

### Post by Carllacan on 2011-10-28
Bump.

Isn't any file I can edit to change the position where a window appears when is opened?

I think I could easily fix the problem with that.

---

### Post by kevinbeard on 2011-11-08
I have exactly the same problem and have not found a solution yet :-(

---

### Post by typhoon_tip on 2011-11-08
Bumped into this problem already many times while trying to "amend" some view settings. I don't know what's causing it, but I know how to fix it:

First, run:
```
gconftool-2 --recursive-unset /apps/compiz-1
```

Then, **open another terminal window**, and run:
```
unity --reset
```

If you remain without a desktop and only with a Nautilus bar at the top of the screen, go to the **first terminal window**, and:
```
ccsm
```

(if is not installed, follow the instructions to install it)

Find the Unity plugin and enable it. Follow the on-screen instruction and fix the conflicts all "in favor of Unity".

Do not close any terminals, logout and login again, everything should be back to normal.

---

### Post by kevinbeard on 2011-11-10
> **typhoon_tip said:**
> Bumped into this problem already many times while trying to "amend" some view settings. I don't know what's causing it, but I know how to fix it:

First, run:
```
gconftool-2 --recursive-unset /apps/compiz-1
```

Then, **open another terminal window**, and run:
```
unity --reset
```

If you remain without a desktop and only with a Nautilus bar at the top of the screen, go to the **first terminal window**, and:
```
ccsm
```

(if is not installed, follow the instructions to install it)

Find the Unity plugin and enable it. Follow the on-screen instruction and fix the conflicts all "in favor of Unity".

Do not close any terminals, logout and login again, everything should be back to normal.

Great...that worked.  It was a bit scary for a second as I lost unity, but killing and restarting lightdm seems to sort that out

---

