---
title: "Unity disappeared from my user profile."
date: 2011-11-13
forum: Desktop Environments
---

### Post by Malfriv on 2011-11-13
I'm a new Ubuntu user. I was working with GIMP photo editor, and firefox simultaneously when my computer crashed. I had no other choice than to switch off manually. When I restarted ubuntu I couldn't find the Launcher, nor the dashboard and all the icons on the Menu bar disappeared. I can't therefore start any application. i tried opening a guest session and there they were. I'm barely learning Ubuntu, if anyone know how to solve this problem i'll appreciate it.

---

### Post by yanom on 2011-11-13
> **Malfriv said:**
> I'm a new Ubuntu user. I was working with GIMP photo editor, and firefox simultaneously when my computer crashed. I had no other choice than to switch off manually. When I restarted ubuntu I couldn't find the Launcher, nor the dashboard and all the icons on the Menu bar disappeared. I can't therefore start any application. i tried opening a guest session and there they were. I'm barely learning Ubuntu, if anyone know how to solve this problem i'll appreciate it.

try this -

right click on the desktop and create a launcher. Put ```
unity
```

into the Command box. name it whatever you want. Then click that icon. It should bring back the unity bar.

If you decide you're just <snip> fed up with unity, try XFCE desktop. look up xubuntu-desktop in the Synaptic Package manager, installing that installs the whole XFCE suite (warning: that's a big download)

---

### Post by Copper Bezel on 2011-11-13
That won't work for a couple of reasons. First, he'd need to have a text document in his templates folder, and second, you didn't tell him to mark it executable.

If Compiz is running, you can press Ctrl+Alt+T to bring up a terminal. Try it, then run unity --replace.

If no terminal appears, press Ctrl+Alt+F1 to switch to a virtual terminal. Log in and run

```
export DISPLAY=":0"
unity --replace
```

to restart Unity, then hit Ctrl+Alt+F7 to get back to your desktop.

Edit: If those didn't work, try [this guide]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html").

---

### Post by yanom on 2011-11-13
btw, you aren't the first person to be mad at Unity. Try XFCE, or KDE, or something.
That being said, welcome to Ubuntu. Hope you like it.

---

### Post by ottosykora on 2011-11-14
> **yanom said:**
> btw, you aren't the first person to be mad at Unity. Try XFCE, or KDE, or something.
That being said, welcome to Ubuntu. Hope you like it.

I wanted to say something similar:

Be happy you lucky guy! You managed something others are trying to do without success!   ;-)

---

