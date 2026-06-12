---
title: "Font Sizes under sudo"
date: 2006-02-04
forum: Desktop Environments
---

### Post by TheSoko on 2006-02-04
Got annoyed with Gentoo and wiped it for Kubuntu earlier this week, and I'm pretty happy with it so far.

However, when I run apps through sudo, like Synaptic or if I click the 'Administrator Mode' button in systemsettings, it appears that KDE is keeping a different set of font settings than my normal user. Unfortunately the administrator mode button goes disappears when I go to the Font settnigs. Any ideas?

---

### Post by sfabel on 2006-02-04
Run

```
sudo kcontrol
```

from a konsole and adjust the font settings of the root user that way. Maybe that helps?

Cheers,
Stephan

---

### Post by TheSoko on 2006-02-04
Tried that... It comes up but the list on the left side is completely empty.

```

$ sudo kcontrol
Password:
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
ERROR: Communication problem with kcontrol, it probably crashed.
john@Kibeth:~$ kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kcontrol: ERROR: : couldn't create slave : Unknown protocol 'file'.
kcontrol: ERROR: : couldn't create slave : Unknown protocol 'file'.

```

---

### Post by obibok on 2006-02-05
[http://linuxtuneup.blogspot.com/2005/11/sudoed-apps-look.html](http://linuxtuneup.blogspot.com/2005/11/sudoed-apps-look.html)

---

### Post by TheSoko on 2006-02-07
That worked. Thanks!

---

