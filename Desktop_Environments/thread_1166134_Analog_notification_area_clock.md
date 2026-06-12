---
title: "Analog notification area clock"
date: 2009-05-21
forum: Desktop Environments
---

### Post by ManyBeers on 2009-05-21
I like to run my panel in full transparency but when I do I cannot
see the standard Gnome clock unless I hover over it with the mouse. Is there an analog clock app that I can download that will show up without hovering. Thanks

[IMG][[IMG]http://img507.imageshack.us/img507/8278/screenshotalx.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshotalx.png)[/IMG]

---

### Post by mcduck on 2009-05-21
I've never seen analog clock applet for Gnome-panel.

But one thing you could do is changing the clock's text color into something that you can see with transparent panel and dark background. ;)

If you want to do that, create a file called .gtkrc-2.0 in your home directory, and then paste following piece of code into that file:

```
style "panel-clock"
{
  fg[NORMAL] = "#ffffff"
}
widget "*.clock-applet-button.*" style "panel-clock"
```
(you can of course change the "ffffff" to any color you like)

After that save the file, log out and back again and your clock applet should now use the new color.

---

### Post by ManyBeers on 2009-05-21
> **mcduck said:**
> I've never seen analog clock applet for Gnome-panel.

But one thing you could do is changing the clock's text color into something that you can see with transparent panel and dark background. ;)

If you want to do that, create a file called .gtkrc-2.0 in your home directory, and then paste following piece of code into that file:

```
style "panel-clock"
{
  fg[NORMAL] = "#ffffff"
}
widget "*.clock-applet-button.*" style "panel-clock"
```
(you can of course change the "ffffff" to any color you like)

After that save the file, log out and back again and your clock applet should now use the new color.

Thanks mcduck I will give it a go and report back. Incidentally I actually looked in gconf-editor to see If I could change the font color of the clock app in there. i did not find any way to do it.

---

### Post by ManyBeers on 2009-05-21
> **mcduck said:**
> I've never seen analog clock applet for Gnome-panel.

But one thing you could do is changing the clock's text color into something that you can see with transparent panel and dark background. ;)

If you want to do that, create a file called .gtkrc-2.0 in your home directory, and then paste following piece of code into that file:

```
style "panel-clock"
{
  fg[NORMAL] = "#ffffff"
}
widget "*.clock-applet-button.*" style "panel-clock"
```
(you can of course change the "ffffff" to any color you like)

After that save the file, log out and back again and your clock applet should now use the new color.
Worked beautifully. Thanks mcduck. By the way is there a way to change the font color using gconf-editor?

---

### Post by mcduck on 2009-05-21
Great that you got the problem solved.

Using the gtkrc file is the only way to customize panel applet colors I know. If there was option for it in gconf-editor I would certainly have told that one to you instead of this trick that requires messing around with hidden files and strange bits of code. :)

By the way, based on your screenshot you have the same problem with the Window List applet? It can be solved in the same way:

```
style "panel-applet"
{
  fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "panel-applet"
widget "*PanelApplet*" style "panel-applet"
```
(this should change text color of most panel applets)

---

### Post by ManyBeers on 2009-05-21
> **mcduck said:**
> Great that you got the problem solved.

Using the gtkrc file is the only way to customize panel applet colors I know. If there was option for it in gconf-editor I would certainly have told that one to you instead of this trick that requires messing around with hidden files and strange bits of code. :)

By the way, based on your screenshot you have the same problem with the Window List applet? It can be solved in the same way:

```
style "panel-applet"
{
  fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "panel-applet"
widget "*PanelApplet*" style "panel-applet"
```
(this should change text color of most panel applets)

What do i name the file? Do I just paste it in the same file as the clock code?

Yes when all apps are minimized they don't show on the panel.
But if an app is opened it does show on the panel. I'm not sure if I will change that but just in case i will copy your code and save it if i deceide to change things. thanks again

---

### Post by mcduck on 2009-05-21
> **ManyBeers said:**
> What do i name the file? Do I just paste it in the same file as the clock code?

Yes when all apps are minimized they don't show on the panel.
But if an app is opened it does show on the panel. I'm not sure if I will change that but just in case i will copy your code and save it if i deceide to change things. thanks again

Put it into the same file.

That file simply works as a place where you can put any theme configurations that you wish to override settings defined by your current GTK theme. (GTK themes actually each have their own gtkrc file located in that theme's directory.) Also people who are not using Gnome can use that file to configure colors for any GTK applications they use.

---

### Post by ManyBeers on 2009-05-21
> **mcduck said:**
> put it into the same file.

That file simply works as a place where you can put any theme configurations that you wish to override settings defined by your current gtk theme. (gtk themes actually each have their own gtkrc file located in that theme's directory.) also people who are not using gnome can use that file to configure colors for any gtk applications they use.

ok

---

### Post by hatrickmcmullet on 2011-06-01
Knowing how to solve this problem (I also use a transparent panel) makes me wonder what else about the clock (or more generally, in gnome) i can customize. Is there a resource for this?

---

