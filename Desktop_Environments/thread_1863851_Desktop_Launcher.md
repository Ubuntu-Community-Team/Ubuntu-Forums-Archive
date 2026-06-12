---
title: "Desktop Launcher"
date: 2011-10-18
forum: Desktop Environments
---

### Post by makitso on 2011-10-18
OK, I am a bit new to Lubuntu and LXDE.  

One of the things that irked me about Gnome 3 was them dropping the ability to put an icon on the desktop (not on the launcher or dock) and to be able to launch an app with it.  In G2 you simply right clicked anywhere and you were good to go.

So, I tried xubuntu and xfwm4 has this capability.  So on to lubuntu and openbox.  

As stated before, I really like lubuntu.  And as I test it I am finding that it really has most of the capabilities I need in a desktop.  

My question is, am I missing something, does openbox provide the ability to create a launcher anywhere on the desktop outside of a panel?    If not are there any add ons to do this?

Rob

---

### Post by Copper Bezel on 2011-10-18
It's actually nothing to do with the window manager. Each environment has its own app managing the desktop, and that application draws the wallpaper and provides the desktop icons if present. In XFCE, that's xfdesktop. In Gnome 2, it's actually a special Nautilus window. 

I don't know LXDE, but as I understand it, the desktop provides a right-click menu, but not icons? You'll need to figure out what application that is and replace it with one more to your tastes. Whether or not you *can* swap it out for something else (since LXDE's session launcher thingy is binary, rather than an editable script) is another matter. 

As for what to run, you could just run xfdesktop in place of whatever LXDE is using. I know there's another, lighter-weight one I'm forgetting, but it's not coming to mind. Rox Filer can draw desktop wallpaper as well, if you want to try that.

---

### Post by SteveDee on 2011-10-19
> **makitso said:**
> 
My question is...create a launcher anywhere on the desktop outside of a panel?
Rob

Open a terminal and type something like this:-
```

lxshortcut -i  ~/Desktop/TestFM.desk

```
In the Application Shortcut dialog that opens, enter:-
Name: Test Launcher
Command: pcmanfm

A launcher will appear on your desktop from which you can launch PcManFM.
You can also right click the icon, open in a text editor, and make changes to it.

Some people will hate this.... I hate unnecessary desktop icons!

---

### Post by countryranger on 2012-01-02
I have found this work around for LXDE/Lubuntu:

in terminal (CTRL+ALT+T)
```
sudo apt-get install alacarte 
```

Run Alacarte

-Create a new menu called "test" or whatever
-Open the menu and add an item just as you would in Gnome2 (fill in the blocks)
-Open your applications menu by clicking on the icon in lower left of the screen (or where ever you may have moved it to) and mouse over the new menu item
-right click and choose Add to Desktop

---

### Post by Rodney9 on 2012-01-02
See - [http://forum.lxde.org/viewtopic.php?t=182&f=3](http://forum.lxde.org/viewtopic.php?t=182&f=3)
and
[http://forum.lxde.org/viewtopic.php?f=8&t=31151&p=36938&hilit=shortcuts#p36938](http://forum.lxde.org/viewtopic.php?f=8&t=31151&p=36938&hilit=shortcuts#p36938)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by abbadd0n1 on 2012-01-25
SteveDee solution works. You can name the .desk file anything you need. Need more places like this. Took forever to get Compiz to work on Lubuntu 11.10. Now need to figure out how to edit the menus LOL..

---

