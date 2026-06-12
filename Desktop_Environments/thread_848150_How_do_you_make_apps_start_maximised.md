---
title: "How do you make apps start maximised?"
date: 2008-07-03
forum: Desktop Environments
---

### Post by Carl H on 2008-07-03
Is there a way that I can get an app to start maximised when I start it from the icon on my panel? 

With some apps, you can add -maximized or similar to the launcher command, but not every app supports this. 

It's Emacs that I want to start maximized, if that helps.

---

### Post by pauper on 2008-07-19
In GNOME you can bind a key sequence to make an application become fullscreen
or maximized via:

System--Preferences--Keyboard Shortcuts

Look for 

Window Management: Toggle fullscreen mode or Toggle maximization state

For something more elaborate check out "devilspie" and "wmctrl".

```
sudo apt-get install devilspie wmctrl
```

---

