---
title: "In XFCE, how do I assign keyboard shortcuts?"
date: 2007-06-02
forum: Desktop Environments
---

### Post by wersdaluv on 2007-06-02
In XFCE, how do I assign keyboard shortcuts for music players, volume control, maximize windows, etc.

In "Shortcuts" menu in the Keyboard preferences window, the shortcuts seem only to be for running applications.

---

### Post by x1a4 on 2007-06-02
Most media applications have command-line options or a separate script/binary to control the app.  

For example: 

Xfmedia comes with **xfmedia-remote** wich is used to control it.  

I have **xfmedia-remote --next** assigned to the 'Next Track' button on my keyboard
**xfmedia-remote --stop** to the 'Stop' button, etc.

See your media player's documentation and configure your shortcuts in 'Keyboard Preferences'

---

### Post by neoflight on 2007-06-06
Could you please tell me how to assign shortcut for opening the terminal. I usually have Alt+F3 for it in gnome and kde. When i go to keyboard preferences, it tells me to add new theme? and its not working. Does it use all the themes listed on only one at a time. Thanks

---

### Post by aysiu on 2007-06-06
In the keyboard preferences, go to **Shortcuts** and then **Add**. Name your new profile... anything you want (just not *Default*, because that already exists). In the attached screenshot, the user named the new profile *Zenwalk*. Once you do that, you can easily assign shortcuts to any command you want. You can make Alt-F3 launch ```
xfce4-terminal
```

---

### Post by neoflight on 2007-06-06
Thanks a lot ... 

oops...I had just figured that one and was about to post it. you beat me on it...
The only difference was that i used the command for the terminal !!!!

```
exo-open --launch TerminalEmulator
``` 

I got it from the "terminal quick launcher" by looking at the properties (right click)..

---

### Post by wersdaluv on 2007-06-06
> **aysiu said:**
> In the keyboard preferences, go to **Shortcuts** and then **Add**. Name your new profile... anything you want (just not *Default*, because that already exists). In the attached screenshot, the user named the new profile *Zenwalk*. Once you do that, you can easily assign shortcuts to any command you want. You can make Alt-F3 launch ```
xfce4-terminal
```

aysiu, can you give me the link from where you got that theme from?

---

### Post by aysiu on 2007-06-06
> **wersdaluv said:**
> aysiu, can you give me the link from where you got that theme from?
I didn't. I got that image from a Google search, since I'm not using Xubuntu (right now I've got IceWM on my laptop and Gnome on my desktop).

---

