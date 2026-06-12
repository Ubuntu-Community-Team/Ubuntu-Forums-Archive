---
title: "How to make window list icons only?"
date: 2009-04-23
forum: General Help
---

### Post by PupSpark on 2009-04-23
How would one make the window list (The one by default on the bottom) only show icons to save space on the list?

---

### Post by cwbar_1 on 2009-04-23
Try this. System > Preferences > Appearance > Inaterface & tic dropdown next to Toolbar button labels.

---

### Post by PupSpark on 2009-04-23
> **cwbar_1 said:**
> Try this. System > Preferences > Appearance > Inaterface & tic dropdown next to Toolbar button labels.

That doesn't affect my window list. :(

---

### Post by cwbar_1 on 2009-04-23
Sorry about my confusion and spelling.   The windows list (at the bottom of the screen) shrinks the size of the box based on the number of windows open.  I just opened 18 windows and still had icons and text.  How many windows do you open?  (this question is not asked with any sarcasm.)  I usually just switch desktops when it gets too crowded.

---

### Post by PupSpark on 2009-04-26
No, No. I just want to make it so that the text doesn't show. Just the Icons.

---

### Post by mb_webguy on 2009-04-26
I don't think you can do it, at least not with the Window List applet.  You can group windows to save space, and show only windows on the current workspace, but otherwise you're stuck with the icons and text.

The Window Selector applet is a very compact alternative to the Window List.  It appears as a single button on the panel with the icon of the currently selected window.  If you click it, it expands to show the list of windows.

---

### Post by Shukuyir on 2009-05-12
Hi. Try Dockbar or Dockbarx. Dockbar is a panel applet that lists the applications that are running as icons. When the mouse is held over an application's icon a pop-up shows that lists the windows of the application. They can be installed from a repository you'll have to add to your repository list: [https://launchpad.net/~dockbar-main/+archive/ppa](https://launchpad.net/~dockbar-main/+archive/ppa).

---

### Post by WickedPigeon on 2009-07-28
ahhhh... finally:

```
sudo apt-get install window-picker-applet
```

log off, log back in then choose "Window Picker" from the list of available Panel applets


I knew this existed because Easy Peasy uses it. Just took a little digging to find the name of it.

---

### Post by pelle.k on 2009-08-09
There's also [talika]("http://sourceforge.net/projects/talika/"), but i never could find any actual code, nor a .deb for it.
However, [dockbar]("http://www.gnome-look.org/content/show.php/DockBar+0.21+++%2B+awn+applet?content=97822") and [dockbarx]("http://www.gnome-look.org/content/show.php/DockbarX?content=101604") works very well. I prefer the former, since dockbarx is the experimental version. in dockbarx you can add launchers and have it behave pretty much like the windows 7 task bar.
the stable dockbar panel applet does look much better though. it uses a pure gtk interface, while dockbarx uses some "non native" interface, that in my opinion should be optional.
[https://launchpad.net/~dockbar-main/+archive/ppa](https://launchpad.net/~dockbar-main/+archive/ppa)

---

