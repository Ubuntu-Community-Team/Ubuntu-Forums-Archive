---
title: "Can't configure wine anymore"
date: 2008-07-13
forum: Desktop Environments
---

### Post by gully on 2008-07-13
Hi, I need some help with wine.
I recently configured wine to emulate a virtual desktop of 640x480 (so I could play the original C&C in fullscreen) but now I can't configure wine anymore because the configuration screen is being displayed inside the virtual desktop which cuts of the screen's bottom part so I can't click on "apply" anymore and wine is stuck in 640x480 forever.

Does anybody know of a way to configure wine without the gui, or some other way to fix this?



P.S. I already tried removing and reinstalling wine.

---

### Post by damis648 on 2008-07-13
Could you post a screenshot? I can't quite envision this.

---

### Post by sayakb on 2008-07-13
Try:
```
sudo apt-get purge wine
sudo apt-get install wine
```

---

### Post by gully on 2008-07-13
Sure, here it is

---

### Post by damis648 on 2008-07-13
> **gully said:**
> Sure, here it is

Ah, ok. Try this:
Set the settings to whatever you would like in the Graphics menu, removing or resizing the virtual desktop to your liking. When you are done, press tab until the "Vertex Shader Support" menu is highlighted. When it is highlighted, press Tab **exactly** four times and press enter. Then you should be good to go :popcorn: (After reloading wine config)

---

### Post by gully on 2008-07-13
Tabs, ah, yes of course, why didn't I think of that...

Thanks!

---

### Post by damis648 on 2008-07-13
> **gully said:**
> Tabs, ah, yes of course, why didn't I think of that...

Thanks!

Glad to be of help! :popcorn:

---

