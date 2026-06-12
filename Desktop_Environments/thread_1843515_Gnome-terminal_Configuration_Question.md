---
title: "Gnome-terminal Configuration Question"
date: 2011-09-13
forum: Desktop Environments
---

### Post by grayraven on 2011-09-13
Hey guys,

I have a configuration question about gnome-terminal. I have tried everything I can think of, but haven't had much luck. 

Listed below are the details of my system:
I am running Ubuntu 11.04 with the Unity desktop. I have gnome-terminal set as the default terminal application. I have a keyboard shortcut setup to open the default terminal.

I am looking for a way to start gnome-terminal in the maximized state launching it using the keyboard shortcut. I can launch it maximized using the menu launcher.

After searching around, I thought the best way to do this was to use gsettings to edit the org.gnome.desktop.default-applications.terminal entry and add --maximize to the exec-arg key. After verifying the setting, I logged out. After logging back in, I noticed that the setting had not taken effect.

Any thoughts?

Thanks in advance,

James

---

### Post by Zeta-K on 2011-09-13
use devilspie. It recognizes programs by their name whenever they're opened and changes how their window is handled according to whatever configurations you set. So you could make it so that whenever you open gnome-terminal, it detects it opening and maximizes it.

---

### Post by fdrake on 2011-09-13
edit your shortcut and put in the command field
```

gnome-terminal --maximize

```

---

### Post by Krytarik on 2011-09-13
> **grayraven said:**
> 
I am running Ubuntu 11.04 with the Unity desktop.
> **Zeta-K said:**
> use devilspie.
Devilspie is for Metacity, not Compiz/Unity. ;-)

Luckily, it's a lot easier with Compiz: Install "CompizConfig Settings Manager" if not already done so, then set the option "Maximized" of the plugin "Window Rules" to
```
(class=Gnome-terminal & type=Normal)
```and enable those plugin.

Greetings.

---

### Post by grayraven on 2011-09-13
Hey fdrake,

I set the menu shortcut to start maximized, and that works fine. However, when I use my keyboard shortcut gnome-terminal still starts with the default size. I believe this is due to it using the default application arguments which are currently set to '-x'. I tried using gsettings to update these to include the '--maximize' option, but haven't had much luck.

Thanks,

James

---

### Post by fdrake on 2011-09-13
> **grayraven said:**
> Hey fdrake,

I set the menu shortcut to start maximized, and that works fine. However, when I use my keyboard shortcut gnome-terminal still starts with the default size. I believe this is due to it using the default application arguments which are currently set to '-x'. I tried using gsettings to update these to include the '--maximize' option, but haven't had much luck.

Thanks,

James
what is the command for you keyboard shortcut?
same as the icon shortcut?

---

### Post by grayraven on 2011-09-13
Hey Zeta-K and Krytarik,

Thanks for the advice on both devilspie and the compiz manager. I am testing out the compiz solution, and will let you guys know if that fixes it.

I am somewhat shocked that I can't just edit the default application arguments. Something to play around with on another day.

Thanks again,

James

---

### Post by grayraven on 2011-09-13
I just wanted to let you guys know the compiz settings manager setting as outlined by Krytarik solved the issue I was having. In case anyone else needs it, the package for the compiz settings manager is:

```
 sudo apt-get install compizconfig-settings-manager 
```

The rest of the instructions should allow you to finish the configuration. Thanks again to everyone for the help.

James

---

