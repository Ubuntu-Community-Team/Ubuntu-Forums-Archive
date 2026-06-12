---
title: "Anyway to get shadow effects without the other stuff?"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by ogwilson on 2008-02-09
For the shadow under the 2 main panels and the ones that lie under windows/menus. Can i get those without having Windows fade in/out from view/without compiz? I really wanna reserve some resources, but i kinda need shadows.

---

### Post by rainwalker on 2008-02-10
Try researching something called xcompmgr, I heard it draws shadows and can do a few fade effects but isn't full-blown like Compiz

---

### Post by ingvildr on 2008-02-10
Or install compiz settings manager and turn off all the effects except shadows.

---

### Post by rainwalker on 2008-02-10
> **ingvildr said:**
> Or install compiz settings manager and turn off all the effects except shadows.

Oh yeah, I hadn't thought of that :)

---

### Post by BobCFC on 2008-03-08
The latest version of Metacity gives you drop shadows and true transparency for things like the terminal.  It also allows AWN  and screenlets... but without the overhead of wobbly windows etc.

You can turn it on in Hardy Heron I have not got gutsy anymore sorry I can't check. 

To enable in Hardy you have to tick a box in GCONF:   press Alt-F2 and type gconf-editor.  Then goto Apps->Metacity->General  and tick 'compositing manager'.   

If you have your 3D drivers installed you should see instant drop shadow!!

---

### Post by ShodanjoDM on 2008-03-08
Maybe this will help you:

**[Howto: install the latest metacity in Gutsy (and get a built-in composite manager)]("http://ubuntuforums.org/showthread.php?t=648364&highlight=metacity+composite+gutsy")**

---

