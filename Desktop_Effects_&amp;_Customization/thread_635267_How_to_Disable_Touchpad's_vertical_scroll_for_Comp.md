---
title: "How to Disable Touchpad's vertical scroll for Compiz's Roate Cube function"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by radlations on 2007-12-08
So when I type on my laptop or reach for a key while on the desktop. My cube rotates. And it gets really annoying.

How can I disable the rotate cube via vertical scroll function in compiz without having to disable the vertical scrolling function completely.

---

### Post by mgmiller on 2007-12-08
If you haven't already installed it, install the compizconfig-settings-manager package.

```
sudo apt-get install compizconfig-settings-manager
```

Then go to System > Preferences > Advanced Desktop Effects Settings

Go to the section labeled Desktop and uncheck the Viewport Switcher.

That should stop the rotation when your cursor is on the desktop and you hit the scroll feature of your touchpad. 

At least it stops this activity for the scroll wheel of a mouse and I think the edge of the touchpad does the same thing.

Good Luck.

---

### Post by radlations on 2007-12-08
Wow thanks. Problem solved.

---

### Post by metalf8801 on 2008-02-19
> **mgmiller said:**
> If you haven't already installed it, install the compizconfig-settings-manager package.

```
sudo apt-get install compizconfig-settings-manager
```

Then go to System > Preferences > Advanced Desktop Effects Settings

Go to the section labeled Desktop and uncheck the Viewport Switcher.

That should stop the rotation when your cursor is on the desktop and you hit the scroll feature of your touchpad. 

At least it stops this activity for the scroll wheel of a mouse and I think the edge of the touchpad does the same thing.

Good Luck.

Thank you this also helped me

---

### Post by funnypanks on 2008-04-08
> **mgmiller said:**
> If you haven't already installed it, install the compizconfig-settings-manager package.

```
sudo apt-get install compizconfig-settings-manager
```

Then go to System > Preferences > Advanced Desktop Effects Settings

Go to the section labeled Desktop and uncheck the Viewport Switcher.

That should stop the rotation when your cursor is on the desktop and you hit the scroll feature of your touchpad. 

At least it stops this activity for the scroll wheel of a mouse and I think the edge of the touchpad does the same thing.

Good Luck.
YES!!! this has been pissing me off since feisty fawn i think. it worked and now i am happy.

---

