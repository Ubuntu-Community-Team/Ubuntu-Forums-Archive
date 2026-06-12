---
title: "[SOLVED] Desktop not loading"
date: 2009-01-06
forum: General Help
---

### Post by Archangel013 on 2009-01-06
I didn't see this posted already, so I'm going to give it a go.

I'm a Linux newbie, and I was trying to customize the look of Kubuntu cause the default themes got old. I had already had Compiz and all that stuff installed for a long time, it was working fine, everything was great. But then I installed deKorator today, it screwed stuff up with Compiz, so I did an "sudo apt-get remove kwin", and now when I try to log in, it just opens a konsole window. No desktop loads, no panel, no programs, nothing. 

I have no idea what I did, and I doubt uninstalling a program caused the entire desktop to fail, so any help would be greatly appreciated.

---

### Post by lykwydchykyn on 2009-01-06
I'm not sure what of KDE depends on kwin, but I'd suspect removing it might remove a lot of packages.  You could try installing kubuntu-desktop to recover whatever parts of kde might have gotten removed:
```

sudo aptitude install kubuntu-desktop

```

---

### Post by tuxxy on 2009-01-06
Try installing kwin again or the kubuntu-desktop package.

---

### Post by Archangel013 on 2009-01-06
Alright, installing kubuntu-desktop reinitialized the GUI (Thank you :)), but there are still no toolbars at the top (window decorations, I guess. Toolbars with the minimize, maximize, and close buttons). All my old settings with Compiz are (to my knowledge) back to the way they used to be.

The Window Decorations tab is still under system settings, just the toolbars aren't present... Any ideas?

EDIT: Normally, restarting fixes it, but in this case, restarting both the server and the entire computer did nothing.

---

### Post by Archangel013 on 2009-01-07
Ok, my bad. Apparently the Compiz engine was uninstalled, so I just had to reinstall that... Thanks for your help, you can probably mark this thread as solved now :)

---

### Post by chamber on 2009-01-07
You can mark it as solved by using the thread tools.

---

