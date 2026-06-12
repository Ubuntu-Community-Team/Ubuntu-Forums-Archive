---
title: "Disable alt-click in Xubuntu 9.04"
date: 2009-09-08
forum: Desktop Environments
---

### Post by Enk on 2009-09-08
Hi

How can I disable alt-click (moving windows) in Xubuntu 9.04? I have tried to create a file ~/.config/xfce4/xfwm4/xfwm4rc with the content:
```

cycle_minimum=false
cycle_hidden=false
easy_click=false
focus_hint=false
prevent_focus_stealing=true
raise_with_any_button=false

```

But this didn't seem to fix it :/

Really need alt-click for using Blender on my laptop :)

---

### Post by Enk on 2009-09-09
bump :(

---

### Post by bagy on 2009-10-11
Go to window manager --> Accessibility and change from Alt key to None.

---

### Post by phoinx on 2010-09-09
Today (10.04) this is: Applications > Settings > Xfce 4 Settings Manager > Window manager Tweaks > Accessibility tab.

Thanks!

---

### Post by scacinto on 2010-12-11
As of now, (at least in PureDyne) this is 

Settings->Xfce 4 Settings Manager->Window Manager Tweaks->Accessibility-> and change Key used to grab... to "none"

---

### Post by LarsEriksson on 2011-02-21
Is it possible to disable this for only a specific window ?

remotedesk in this case.

Using adobe programs via remotedesk and alt + zoom (zoom out) does not work. kinda annoying.

---

