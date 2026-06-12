---
title: "Beryl window separation on corner when rotating."
date: 2007-02-03
forum: Desktop Environments
---

### Post by Kossilar on 2007-02-03
Hello everybody!

I'm having a strange but simple problem with Beryl. When I rotate the cube, the windows raise slightly off the cube, but if they're sitting on the corner of the cube, the window is divided in two... Its kind of ugly. 

It seems like this happened as a result of one of the updates, but I can't for the life of me figure out how to fix it. 

When I first installed Beryl, windows that were on different sides of the cube would stay together, even when they were raised.

Does anybody know how to fix this?

Any help is much appreciated, thanks.

:)

---

### Post by Waappu on 2007-02-03
Hi

Try to disable 3D Effect plugin.
- Open Beryl Setting Manager
- Go to Visual Effects tab
- Uncheck 3D Effect plugin

---

### Post by Kossilar on 2007-02-03
Well I still want it to use the 3D effect. I just don't want it to cut the window in half.

---

### Post by Kossilar on 2007-02-05
Is anybody else having this problem?

---

### Post by tenjin1 on 2007-02-07
Im having the same problem here at the moment...the window if left on edge of cube is cut in half. I know this is a simple fix..but can;t find the setting for the life of me!!!

Anyone???

---

### Post by tenjin1 on 2007-02-07
..And it's not the 3D effect (even though disabling it does fix it, but turns off everything you want on) ... it was wrapping the window around the corner before with 3D effect on.

---

### Post by tenjin1 on 2007-02-07
Nevermind....

I just started fresh and cleared my settings by entering:

```
mv ~/.beryl ~/.berylbroke

```

then restart beryl

---

### Post by Kossilar on 2007-02-17
Yeah that does it. 

But which setting is it that causes that problem???

Could be a big help if we could find it.

---

### Post by tenjin1 on 2007-02-17
I know, it could be a great help....

I think it has something to do with EITHER OR BOTH:

1. the "Zoom" option (Distance cube should be zoomed out while rotating)

2. the distance of the pages (desktop items) ontop of the cube (i.e. the gap between the pages and the desktop surface, how far raised up off desktop) I forget the name of that option

The further away on these...I think will break the window in half on the corner.

---

