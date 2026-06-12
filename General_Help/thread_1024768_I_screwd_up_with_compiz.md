---
title: "I screwd up with compiz"
date: 2008-12-29
forum: General Help
---

### Post by hyperdude111 on 2008-12-29
I was trying to use the reflections pack so i was applying transparrency to all windows in compiz.
I wasn't paying full attention so i didn't realise i had set the value to 100% transparency. the next thing i know is everything is transparrent it is only black. 

I used Alt-Ctrl-Backspace to go back to gdm which is fine. 

Gnome failsafe is also like this.

I have installed KDE4 which is working fine as it uses KDE compiz not gnome compiz, this means that although kde works fine it can not change the gnome settings for compiz.

I much prefer gnome so i would rather NOT re-install and NOT use kde as my main windows manager.

Thanks

~Hyper~

---

### Post by iponeverything on 2008-12-29
```
metacity --replace 
```

should turn it off from the command line. Ctrl-alt-F2

then use the gconf-editor to change the transparency back.

```
sudo apt-get install gconf-editor
```

schemas -> compiz -> apps -> plugins

You can do a search in gconf-editor. I would just turn off the plugin in question.

---

### Post by hyperdude111 on 2008-12-29
I fixed the problem, I had to create a root account while in kde then i had to log in as root to gnome, I started up the package manager and removed all traces of compiz.

When i logged in as myself again it was back to normal

The above method would not work as i would not be able to see anything and being unable to see anything i would not be able to even enter terminal

---

### Post by adrian.todireanu on 2008-12-29
true, true


so, in other words:
don't ever make your windows completely transparent!!!!!

---

### Post by iponeverything on 2008-12-30
> The above method would not work as i would not be able to see anything and being unable to see anything i would not be able to even enter terminal


Here something that might be useful for you to know in the future.

While in the GUI type CTRL-ALT-F2 this will open vty-2 on a virtual terminal that you can see. Then type CTRL-ALT-F7 to switch back to the GUI.

---

