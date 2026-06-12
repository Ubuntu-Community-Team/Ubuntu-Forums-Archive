---
title: "install/remove Kubuntu"
date: 2009-05-09
forum: General Help
---

### Post by StormRoBoT2 on 2009-05-09
to install kubuntu in ubuntu i have done this

```
sudo apt-get install kubuntu-desktop
```

but if i dont wan this how to remove this? will my ubuntu still be the same?

will my application in ubuntu accessible on kubuntu?

---

### Post by SanJuan on 2009-05-09
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Use google next time.

---

### Post by StormRoBoT2 on 2009-05-09
> **SanJuan said:**
> [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Use google next time.

still one more question their dude

```
but if i dont wan this how to remove this? will my ubuntu still be the same?
```

---

### Post by Alterax on 2009-05-09
> **StormRoBoT2 said:**
> to install kubuntu in ubuntu i have done this

```
sudo apt-get install kubuntu-desktop
```

but if i dont wan this how to remove this? will my ubuntu still be the same?

will my application in ubuntu accessible on kubuntu?

You can access ubuntu apps from kubuntu, but as GNOME is the ubuntu standard (and kubuntu uses KDE), there are some problems with full integration of those apps into the desktop.

You can remove kubuntu with **sudo apt-get purge kubuntu-desktop**.  I recommend following it up with a **sudo apt-get install ubuntu-desktop gdm** before rebooting, just to make sure everything important is still in place.

Finally, you may have issues with your bootup screen saying kubuntu instead of ubuntu.  That can, I believe, be changed in the startup manager.

---

### Post by DeMus on 2009-05-09
> **StormRoBoT2 said:**
> still one more question their dude

```
but if i dont wan this how to remove this? will my ubuntu still be the same?
```

If you read the page the link is pointing to, at the bottom you find a way to remove the Kubuntu desktop manager. Just read it carefully and follow the instructions.

---

