---
title: "Is there any way that I can remove the title bar of the gnome-terminal"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by chinese_ys on 2007-08-14
Hi, guys

I just want to remove the title bar of the terminal, when I open it. How can I do that?

So any advise will be appreciated.

---

### Post by chinese_ys on 2007-08-15
no body uses this kind of stuff?

bump!

---

### Post by steveneddy on 2007-08-15
Right click inside the terminal window, Edit Current Profile.

Go nuts

---

### Post by chinese_ys on 2007-08-15
> **steveneddy said:**
> Right click inside the terminal window, Edit Current Profile.

Go nuts

Thanks for replying me. But can you tell me which item in the terminal Profile controls this?

---

### Post by mannheim on 2007-08-16
I know you can do this using compiz. compiz allows you to draw the decorations (i.e. title bar) only on windows that match a criterion (e.g. all except gnome-terminal windows, or whatever).

---

### Post by notwen on 2007-08-16
Tilda allows one to create a terminal(w/o window borders/decorations) on one or all workspaces, whether to create it always-on-top and you use x & y coordinates to tell tilda where you want your terminal to be.  Tilda website [here]("http://tilda.sourceforge.net/wiki/index.php/Main_Page").  Hope this helps =]

```
sudo apt-get install tilda
```

---

### Post by heinig on 2007-08-16
> **chinese_ys said:**
> Hi, guys

I just want to remove the title bar of the terminal, when I open it. How can I do that?

So any advise will be appreciated.

Changing the command to "gnome-terminal --hide-menubar"  will do that... 
Just change your launcher.

---

### Post by chinese_ys on 2007-08-16
> **heinig said:**
> Changing the command to "gnome-terminal --hide-menubar"  will do that... 
Just change your launcher.

Thanks, but I want to remove the title bar not the menubar.

---

### Post by chinese_ys on 2007-08-16
> **notwen said:**
> Tilda allows one to create a terminal(w/o window borders/decorations) on one or all workspaces, whether to create it always-on-top and you use x & y coordinates to tell tilda where you want your terminal to be.  Tilda website [here]("http://tilda.sourceforge.net/wiki/index.php/Main_Page").  Hope this helps =]

```
sudo apt-get install tilda
```
Thanks, It seems easy to handle. I will your way.

---

### Post by chinese_ys on 2007-08-18
> **notwen said:**
> Tilda allows one to create a terminal(w/o window borders/decorations) on one or all workspaces, whether to create it always-on-top and you use x & y coordinates to tell tilda where you want your terminal to be.  Tilda website [here]("http://tilda.sourceforge.net/wiki/index.php/Main_Page").  Hope this helps =]

```
sudo apt-get install tilda
```

Hi, Budy

If there is any bug in current version tilda? I installed it but I can not start it either from command line and desktop menu.

---

### Post by 5h4rk on 2007-08-19
Hi, is there any way to get rid of the borders?

[[IMG]http://img475.imageshack.us/img475/173/screenshotdv8.png[/IMG]](http://imageshack.us)
Shot at 2007-08-19

---

### Post by chinese_ys on 2007-08-19
> **5h4rk said:**
> Hi, is there any way to get rid of the borders?

[[IMG]http://img475.imageshack.us/img475/173/screenshotdv8.png[/IMG]](http://imageshack.us)
Shot at 2007-08-19

you can disable that from the notebook boarder option in the configuration file I think. But anyone can tell me why I can not even open it?

---

### Post by 5h4rk on 2007-08-20
Nop, that is not the notebook border :(

---

### Post by notwen on 2007-08-20
> **5h4rk said:**
> Hi, is there any way to get rid of the borders?

[[IMG]http://img475.imageshack.us/img475/173/screenshotdv8.png[/IMG]](http://imageshack.us)
Shot at 2007-08-19

Are you using a compositing manager like Beryl, Compiz, or Compiz-Fusion?  These are known to dramatically add shadow to windows and this is what you're seeing.  Depending on if and which you may be using try changing the settings regarding shadow and see if that helps.  Hope this helps. =]

---

### Post by 5h4rk on 2007-08-20
Oh yeh, I'm using CF.

---

### Post by slowselfip on 2007-12-21
> **chinese_ys said:**
> Hi, guys

I just want to remove the title bar of the terminal, when I open it. How can I do that?

So any advise will be appreciated.

Enter ccsm in the terminal. Go to Window Decoration in the Effects group. Select it by double clicking the icon. Enter !(gnome-terminal) instead of any in the Decoration windows option.

Tip, move the window with alt+mouse.

/Anders

---

