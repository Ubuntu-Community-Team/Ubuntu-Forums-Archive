---
title: "Compiz Fusion (Desktop Cube) and Wallpapoz"
date: 2009-07-07
forum: Desktop Environments
---

### Post by Anaxis on 2009-07-07
Is there any way (addon, update, or even terminal script) to get Wallpapoz (an automated wallpaper switcher with an option to switch wallpaper every time a workspace is switched) to recognise when the workspace is switched using Desktop Cube?

From what I can tell, Compiz recognises that the workspace is being switched, but Wallpapoz does not, and thus I'm stuck on a one minute timer (and I have a LOT of wallpapers). I'd like to be able to have multiple wallpapers active at once (as per the Compiz Configuration option "Wallpaper"), so I can view multiple wallpapers at once when zoomed out via Desktop Cube and Cube Rotate, but be able to switch the wallpaper when using Cube Rotate's <Ctrl><Alt><Right/Left> keys.

---

### Post by Anaxis on 2009-07-09
Still looking for help on this issue...

Anyone?

---

### Post by zangderak on 2010-10-20
I found that restarting the wallpapoz daemon after compiz starts works for me.  Now I'm trying to get wallpapoz to start after compiz on session startup.  Does anyone know how to do this?

---

### Post by Dirol on 2011-02-24
OK, I've got it running on my Fedora. In Ubuntu the solution would be just the same.

If you run the daemon_wallpapoz after the compiz has been initiated it would run just fine.
So I've wrote a simple script, which starts wallpapoz after the 15 second delay.

You need to create file (prefferable in the folder where _daemon_wallpapoz is located (for my case it was /usr/bin/)) and place the next lines in it:

```
#!/bin/bash
# This is a script to make sure, that wallpapoz_daemon starts AFTER then compiz
sleep 15
daemon_wallpapoz
```

So, we've got the script file named by, let's assume: wallpapoz_delay
We'll need to make it executable, so we should run in terminal the command
```

chmod o+x wallpapoz_delay
```

Then add (or edit) the startup command for wallpapoz, which is found in the System->Preferences->Startup Apllications, to run wallpapoz_delay, instead of daemon_wallpapoz.
Hope that helps. BTW, I'm using Compiz-Wallinstead of Compiz-Cube, and wallpapoz works great at detecting switches to another workspace.

---

