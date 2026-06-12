---
title: "Gnome and Metacity windows problems"
date: 2006-12-07
forum: Desktop Environments
---

### Post by aiduciukas on 2006-12-07
Hi! I have one problem, when I want to choose other window, I need to press on windows titlebar, in windows I can press anywhere on window to activate it. How to do this on ubuntu 6.10?

---

### Post by loell on 2006-12-07
i gnome , it still pretty the same , you click it then  it will be the active window, if your dragging, you can press "alt key" then drag the window you like to drag

---

### Post by brottman on 2006-12-07
I guess I don't follow. I can click anywhere in the window to make it active in Gnome. This is on Edgy.

---

### Post by mcduck on 2006-12-07
you'll find options for windows in System/Preferences/Window

---

### Post by CatKiller on 2006-12-07
The default is the behaviour you want. You could try Alt-F2 -> gconf-editor, and look in /apps/metacity/general for the **raise_on_click** key. Tick it if it isn't already.

> Many actions (e.g. clicking in the client area, moving or resizing the window) normally raise the window as a side-effect. Set this option to false to decouple raising from other user interactions. When false, windows can still be raised by an alt-left-click anywhere on the window or a normal click on the window decorations (assuming such clicks aren't used to start a move or resize operation).

---

### Post by aiduciukas on 2006-12-08
any of your ideas isn't wokring ;( what I should do?

---

### Post by CatKiller on 2006-12-08
Some people have suggested that their similar problems (raise_on_click true but not working) happened with keyboard layout changes. Others have suggested that it happened when they tried out XGL/Beryl/Compiz. There's nothing particuarly conclusive.

You could try changing focus_mode to "mouse" or "sloppy", but I don't know for sure that it will help. Sorry.

---

### Post by aiduciukas on 2006-12-08
I've just edited my startup and disabled startup prpgram: xmodmap... . And all works, btw thanks guys!

---

