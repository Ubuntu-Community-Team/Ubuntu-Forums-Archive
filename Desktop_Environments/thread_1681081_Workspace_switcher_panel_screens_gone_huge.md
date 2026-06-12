---
title: "Workspace switcher panel screens gone huge"
date: 2011-02-03
forum: Desktop Environments
---

### Post by facelikebambi on 2011-02-03
Weird one... my 4 WS screens in the bottom panel have suddenly gone really wide. They take up most of the panel now and things are getting squashed when I have a few programs open. 

Can't see any options to adjust the size/width? Using 10.10

Thanks!

---

### Post by facelikebambi on 2011-02-04
Now today the switcher has gone back to normal... and the trash bin has disappeared!

grr!

---

### Post by Frogs Hair on 2011-02-04
To reset panels to defaults open terminal and run.```
gconftool --recursive-unset /apps/panel && killall gnome-panel 

```

---

### Post by facelikebambi on 2011-02-04
That fixed it - thanks!

---

