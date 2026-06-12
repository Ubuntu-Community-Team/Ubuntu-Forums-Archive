---
title: "Emerald titlebar buttons disappear on window restore"
date: 2013-03-13
forum: Desktop Environments
---

### Post by Harp on 2013-03-13
So, I'm trying out Emerald and so far I love it except for two minor problems which can get pretty annoying at times. 

1) When I restore a window from full-screen, the titlebar buttons (minimize, maximize, close) seem to just disappear. I can still click them but I cannot see the buttons. If I minimize the window and then re-open it, the buttons are restored. I've read somewhere about a glitch where if you set the Titlebar Double-Click Action to "Shade" it can cause this problem, and that setting it to "Maximize/Restore" will solve it, but this did not help me at all. Does anyone know what is causing this and/or how to fix it?

2) Also, I don't like the fact that I can't resize borderless windows. I prefer my themes to be borderless but in Emerald, it seems you can't resize via the edges without at least a 1px border. As I said, it's a minor problem but it gets on my nerves sometimes trying to grab this tiny 1px border. Compiz does not seem to have this trouble.

---

### Post by Harp on 2013-03-15
bump

---

### Post by Frogs Hair on 2013-03-15
What Ubuntu version ? Emerald has not been officially supported since 10.10 and there are currently two ways to install it on 11.10 -12.10 . Either way the official documentation is out dated may not apply at all on new versions of Ubuntu. The PPA (use at your own risk) was a means to make it possible to keep using but the application but, the  developer/s bailed out years ago even though people continue to make themes for it . The following may restore the title bars but I don't know for how long and it is hassle to run the command as well.

```
emerald --replace
```

---

### Post by Harp on 2013-03-15
The emerald --replace command simply sets emerald as the current window decorator over whatever else is already running (presumably compiz). If emerald is already running, I don't think this would be a good option to restore the buttons as simply minimizing a window and re-opening will accomplish this without having to re-start emerald. I'm looking for some kind of conflict that is causing this glitch. 

I am running 12.04 and installed emerald using this guide: [http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html](http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html)

---

### Post by masavini on 2013-07-05
> 1) When I restore a window from full-screen, the titlebar buttons (minimize, maximize, close) seem to just disappear. I can still click them but I cannot see the buttons. If I minimize the window and then re-open it, the buttons are restored. I've read somewhere about a glitch where if you set the Titlebar Double-Click Action to "Shade" it can cause this problem, and that setting it to "Maximize/Restore" will solve it, but this did not help me at all. Does anyone know what is causing this and/or how to fix it?

bump: same issue here (emerald on gnome fallback - ubuntu13.04 64 bit)

---

