---
title: "Force chromium to open from terminal"
date: 2012-03-03
forum: Desktop Environments
---

### Post by andyklaj1985 on 2012-03-03
Hey Guys

Hoping someone could show me the code to open chromium to full screen mode from the terminal.

Have looked at the man page.  I aslo thought that env would be able to do this (wasnt a complete lost investigating as i now understand another command).

There must be a way to control window geometry.  I have a feeling it has something to do with the desktop environment, but unfortuneately that is well beyond the capacity of my knowledge of linux

For what it is worth i am using lubuntu (LXDE)

Kind regards

Andrew

---

### Post by ankspo71 on 2012-03-03
Hi, Try this for the command:
```
chromium-browser --kiosk
```

You can also open a certain URL in kiosk mode:
```
chromium-browser --kiosk ubuntuforums.org
```

That is based on what I found here: [http://ubuntuforums.org/showthread.php?t=1729652](http://ubuntuforums.org/showthread.php?t=1729652)

Here is also this site that shows many command line switches for Chromium:
[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

---

