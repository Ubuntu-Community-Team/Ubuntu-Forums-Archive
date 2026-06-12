---
title: "Ugly windows + progressbar, how to fix?"
date: 2010-12-23
forum: Desktop Environments
---

### Post by KamiKazeKenji on 2010-12-23
I've modified the Radiance theme and installed it, and everything looks wonderful except for one thing. Certain programs have ugly windows and progress bars, as if all window effects were disabled for those windows. The progress bar in GIMP is not affected, but as you can see in the screenshot that I've attached, the Package Manager is affected by this.

This is a slight eyesore, so any help is appreciated. Thanks in advance!

---

### Post by stinkeye on 2010-12-23
If your theme is in ~/.themes you need to make it available to programs run as root.
```
sudo cp -r /home/*[COLOR="Magenta"]username[/COLOR]*/.themes /root
```
[COLOR="#ff00ff"]Change for your username.[/COLOR]

If you copy your theme to **/usr/share/themes** that will also make available to root as well as other users.

---

### Post by KamiKazeKenji on 2010-12-23
Ahh. I see... Your solution did the trick! Your help is greatly appreciated. ^_^_^

---

