---
title: "nautilus desktop stuff"
date: 2009-02-20
forum: Desktop Environments
---

### Post by ducky101 on 2009-02-20
Hi, I have a question.

When I alt+tab I can select "x-nautilus-desktop", this on it's own is not a problem. The problem is that when I click on the desktop it overlays all the other windows (the desktop is a window on its own????). This sucks and is frankly a not so smart feature. How do I make it stop doing this.

I have uninstalled nautilus, but then I also mis the desktop icons and file manager.

Please help, I'm getting crazy because of this.
I have a different machine with centos 5 and gnome 2.16, and the gnome desktop 2.16 is much better.

---

### Post by my window broke on 2009-02-20
you uninstalled nautilus? from what I know, that is a special file manager for gnome. I use it quite often.

---

### Post by my window broke on 2009-02-20
Anyways, so when you select nautilus is made it appear like you had another desktop on top of a desktop? If that happened its because when you invoke nautilus, you open a file manager. I use it to get root file permissions and install fonts and other sys config stuff. Should be able to reinstall it.

---

### Post by ducky101 on 2009-02-20
@my window broke
Nautilus is more than just a file manager. It also manages your desktop. Oh, I also know what a desktop looks like and what a file manager is.

Anyways, what I mean is that the desktop is drawn on top of everything when I click on it, I don't know how to explain it any differently.

Somewhere between gnome 2.16 and nautilus 2.16 and gnome 2.24 some bright mind figured it was smart to draw the desktop on top of everything when clicked on, even on top of other windows. 
My question is how to make gnome/nautilus stop doing this.

I hope this makes it a bit clearer what I mean.

---

### Post by mcduck on 2009-02-20
That definitely isn't a feature, Alt-tabbing should not show the desktop window.. (of course bringing the desktop window to foreground when alt-tabbed is correct behavior, the thing is that you shouldn't be able to alt-tab to it in the first place)

So this sure isn't a case of any developer creating new stupid features but a bug on your computer/setup.

Are you suing Gnome's own alt-tab or some Compiz plugin?

---

### Post by ducky101 on 2009-02-21
No compiz. 
I have the ubuntu netbook-remix.
The problem, I am having is that in a dual screen setup clicking on the desktop puts the desktop on the foreground (over all the windows that I have open). It is the standard installation, nothing fancy. I believe it has something to do with nautilus, because when I uninstall it, it does not happend anymore and clicking on the desktop leaves all the open windows visible.

Thanks
Alex

---

### Post by mcduck on 2009-02-21
Well, it of course has something to do with nautilus as Nautilus is the program that draws the desktop, desktop icons and provides you with right-click menu on the desktop.

But like I said, the bug is in the program that provides the alt-tabbing feature as it's not supposed to include the desktop window.

I don't really know if the netbook remix has some other program to handle the desktop as well, but in normal Gnome removing Nautilus would leave you without any wallpaper or desktop at all. If the netbook-remix uses some other program to handle te desktop by default and you are simply using Nautilus as file manager then you should start it with "nautilus --no-desktop" and also edit all your launchers & menu entries to use that instead of simple "nautilus".

---

### Post by ducky101 on 2009-02-21
OK I will try the --no-desktop switch, thanks.
But like I said, it is **not** just alt-tabbing, also clicking on the desktop makes it do that:( which is what makes it annoying.

Thank you for your help.

Alex

---

### Post by blackened on 2009-02-21
That's a "feature" particular to the netbook remix. It does the same on my eeepc and is very useful.

The point is so you can click on, or alt+tab to, the desktop and have the netbook-launcher app take over the whole screen. If the netbook-launcher process isn't running, then it will bring the desktop to the front instead.

Are you using this on a netbook? If so, then you can always install the regular release of Ubuntu and just add the Array.org kernel post-install. 

What you're describing is not a bug though, it's supposed to work that way.

---

### Post by ducky101 on 2009-02-21
@blackened Thank you, thank you!!!

Finally, now I know.

Yes I am using this on an asus eeepc 1000. I have a larger (23") external monior attached to it.

I was starting the netbook-launcher with the -w switch in window mode. This way I could keep the netbook-launcher on the netbook screen and just use the larger monitor for the main stuff.
That's why it wasn't working like you described :o


Ok, now how do I turn off this particular "feature". 

Thank you again.

Alex

---

