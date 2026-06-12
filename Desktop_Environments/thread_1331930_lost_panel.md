---
title: "lost panel"
date: 2009-11-19
forum: Desktop Environments
---

### Post by ubunewtu on 2009-11-19
im running ubuntu 9.10 ive been playing with it and i deleted my default panel is there a way to get it back or do i have to manually set it up (this all started when i was on ebay and it opened a picture in a seprate window i right clicked in the panel and clicked delete thinking that "panel" refered to the window)

---

### Post by drs305 on 2009-11-19
You can right click on any panel, then New Panel. Then right click on the new panel, select Properties, and place it where you want (or you can drag it).

Once you have it where you want, you can restore the *defaults* with these commands:
```

gconftool-2 --recursive-unset /apps/panel
killall gnome-panel &

```

Once you have added what you want to the panels and want to save the configuration, you can run these commands, which create and then use a file called *panels* on your Desktop. The name and location can be wherever you choose:
To save: 	
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
To restore: 	
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by ubunewtu on 2009-11-20
thank you it worked

---

