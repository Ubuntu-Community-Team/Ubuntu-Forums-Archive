---
title: "firefox starts without window decorations"
date: 2009-01-19
forum: General Help
---

### Post by demios on 2009-01-19
Everything was more or less ok until I accidentally used all the space on my ubuntu partition by downloading the beta of windows 7 and installing rosegarden simultaneously. I guess it overwrote some settings. anyways, I moved the beta to a different partition once it finished, but now when I start firefox it starts basically outside of gnome: overtop of the gnome-panel and without window decorations. Also, it won't let me login to hotmail or deviantart. I tried uninstalling and installing 3b5, but nothing changed.

probably just a setting somewhere for the gnome issues, but the login stuff is annoying. I was thinking of reverting to 8.04 to get my rt kernel back anyways, but in the meantime, any help is appreciated.

---

### Post by adamlau on 2009-01-19
In a terminal window:

```
firefox -safe-mode
```

And of that does not work, create a new profile via:

```
firefox -ProfileManager
```

---

### Post by Yashiro on 2009-01-19
- Revert back to no desktop effects/metacity wm.
- Press F11 a couple of times.
- Hold alt and drag the window down.
- Resize it.

---

### Post by demios on 2009-01-19
> **adamlau said:**
> In a terminal window:

```
firefox -safe-mode
```

And of that does not work, create a new profile via:

```
firefox -ProfileManager
```

First solution worked for first ailment, second for second -- thanks man!

---

### Post by tamccain on 2009-01-19
This actually happened to me the other day and it was a setting in CompizConfig - under 'Workarounds' uncheck the box that says, 'Legacy Fullscreen Support' - that is of course if you are using Compiz

---

