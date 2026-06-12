---
title: "compiz forcing red window border?"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by _deos on 2008-03-18
i just made the switch to linux yesterday and i LOVE it :)

i was tinkering around with compiz when it started forcing a red border on mlp y windows, i tried changing my theme borders but it doesnt do anything

i also did some searching and tried replacing metacity , that fixes it but it stops compiz and all my effects are gone not to mention i reboot and it doesnt save :(

any help would be awesome

thanks!

---

### Post by overdrank on 2008-03-18
> **_deos said:**
> i just made the switch to linux yesterday and i LOVE it :)

i was tinkering around with compiz when it started forcing a red border on mlp y windows, i tried changing my theme borders but it doesnt do anything

i also did some searching and tried replacing metacity , that fixes it but it stops compiz and all my effects are gone not to mention i reboot and it doesnt save :(

any help would be awesome

thanks!

Hi and welcome, are you using emerald as the theme manager?

---

### Post by _deos on 2008-03-18
maybe? iits whatever came bundled with gusty gibbon

is there a way  can check from the terminal?

---

### Post by Therion on 2008-03-18
You could try going into Advanced Desktop Settings and seeing if turning off the Window Decorations plugin helps.

---

### Post by FuturePilot on 2008-03-18
> **Therion said:**
> You could try going into Advanced Desktop Settings and seeing if turning off the Window Decorations plugin helps.

You don't want to disable that plugin. It will get rid of all window decorations and windows will be unmovable.
Try this
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
Restart Compiz
```
compiz --replace
```

---

### Post by rahduke on 2008-03-19
that worked for me! Thanks alot... very good stuff

---

### Post by rahduke on 2008-03-19
ahhhh.... I spoke to soon, It does work great but as soon as i close the terminal window everything goes haywire... I lose my window decoration completely despite the effect being turned on in Advanced Settings.


any help would be appreciated :)

---

### Post by FuturePilot on 2008-03-19
Press Alt+F2 and run
```
compiz --replace
```
from there.

---

