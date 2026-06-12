---
title: "Xfwm4 Not present upon logging in."
date: 2011-09-28
forum: Desktop Environments
---

### Post by TuxIsAwesome on 2011-09-28
I've been having some issues with xfwm4.

It seems to not auto-start when I login to Xfce4/Xubuntu. Recently I had to rename the xfce4 config files and rename the /.local/share/applications menu by adding a .back to each one because my menu was messy, and tainted. That solved the menu problem.

Xfce4's Window Manager did load once the first time I logged into it, but ever since then it hasn't been starting automatically, in fact no window manager starts.

I cant very well add this to the startup applications, since it will apparently also load in Unity and I certainly do not want that to happen. 

I'm certain it's something fairly stupid/obvious/simple that's causing it, but I cannot find what's causing it.

I will not move/rename that .local/share/applications or the .config/xfce4 folder back to their original names in order to fix this however, I don't care for my menu to be cluttered up like that.

---

### Post by 3Miro on 2011-09-28
Xfce4 session has some bad memory.

Try Ctr+F2 and then type
```
xfwm4 --replace
```

This should start xfwm4. Then edit the XFCE session settings to remember the running xfwm4 and make sure xfce doesn't remember the session anymore.

---

### Post by TuxIsAwesome on 2011-10-01
Yay, I did just that and it seems to have fixed the issue.

Now I just need to get my GTK3 apps to use the oxygen-gtk theme in KDE. I have the gtk3 engine for oxygen installed via PPA.

Thanks much!

---

