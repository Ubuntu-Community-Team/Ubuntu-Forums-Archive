---
title: "Synaptic missing after upgrade to hoary"
date: 2005-05-11
forum: Desktop Environments
---

### Post by linuxNewb on 2005-05-11
To be specific, it's just the Synaptic menu item. The ubuntuguide states that it should reside in System -> Administration -> Synaptic Package Manager, but it's not there.

I just upgraded to hoary using the instructions at [http://ubuntuguide.org](http://ubuntuguide.org), and everything else seems to have worked seemlessly -- amazing. Has anyone else had this problem? Is this indicative of a larger issue? How can I add Synaptic to this menu manually? Thanks in advance.

NOTE: I'm on a Compaq Presario 900

---

### Post by blueplazma on 2005-05-11
From a terminal, try running this.
```

sudo apt-get update && sudo apt-get install synaptic
killall --HUP gnome-panel

```

You should now have synaptic in your menu.  In the future, please make sure you try searching the forums first, as I think this question has been answered before.

---

