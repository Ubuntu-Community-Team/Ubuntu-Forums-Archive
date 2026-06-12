---
title: "Help changing Gnome2 settings?"
date: 2011-09-15
forum: Desktop Environments
---

### Post by kalebmcc on 2011-09-15
I've been trying to get Gnome2 to behave the way I want it, but I'm having trouble. I'm very new to Linux and don't know where else to look. I'm running 11.04 Desktop and Gnome 2.

First, I got Slingshot launcher up and running. I love it, it's great. However, I have a couple questions: How can I change the Gnome launcher icon to the Ubuntu button icon in Unity? How can I hotkey it to launch when I press the super key?

Second, I can't get globalmenu for Gnome to work. I've downloaded it, but can't figure out how to build or install it. I've read and attempted multiple tutorials, but none of them seem to work.

Lastly, I'm using Docky as my taskbar. I'd like to get it a little more like the Windows 7 bar, though. Is there some way to make it pop open a list of an applications open windows on left click, rather than right click? Is it possible to have more than two little indicators? 

Thanks in advance!

---

### Post by sanderd17 on 2011-09-15
For a more windows like dock, try dockbarX as AWN plugin.

I don't know how slingshot works.

Where did you download the globalmenu? So we know what type of file you have etc.

---

### Post by kalebmcc on 2011-09-15
I downloaded the 0.7.10 tar.gz from here: [http://code.google.com/p/gnome2-globalmenu/downloads/list](http://code.google.com/p/gnome2-globalmenu/downloads/list)

Also, you don't need to know anything about Slingshot specifically, it's just a standard Gnome launcher using "slingshot" as the command. I just want to know how to change the hotkey for Gnome launchers and where the Ubuntu icon is, basically.

---

### Post by sanderd17 on 2011-09-15
If you unpack it, you will see it has a file INSTALL with the installation instructions.

What you should do is open a terminal, go to the unpaked directory that contains the configure scripts etc with the command cd, so something like

```

cd /home/user/Downloads/gnome-globalmenu/

```

than execute
```

.configure
make 
sudo make install

```

---

### Post by sanderd17 on 2011-09-15
> **kalebmcc said:**
> 

Also, you don't need to know anything about Slingshot specifically, it's just a standard Gnome launcher using "slingshot" as the command. I just want to know how to change the hotkey for Gnome launchers and where the Ubuntu icon is, basically.

There is a program with the name hotkeys I think (I'm now on Gnome-Shell, so I can't test it).

And the Ubuntu logo at /usr/share/icons (somewhere in there, it depends on what iconset you use).

---

### Post by Copper Bezel on 2011-09-15
> For a more windows like dock, try dockbarX as AWN plugin.
Or standalone, since it does that now and he's not using AWN.

You're probably using Compiz, which doesn't make it easy to set Super to run a command, since it's a modifier key. (The same is true of the fallback window manager, Metacity.) The best would probably be to use compizconfig-settings-manager's Commands plugin and set the command "slingshot" to something similarly easy to strike, such as F1, Super+Space, or something of the sort.

To add to sanderd17's comment, he distributor logo icons are usually in Places, for some reason, and could be called "distributor-logo" or "start-here", "ubuntu-start-here", etc.

Edit: You shouldn't have to install anything for the global menu. It ships with 11.04. When you right-click and select "Add to Panel", it's listed as "Indicator Applet Menu."

---

### Post by Krytarik on 2011-09-15
> **kalebmcc said:**
> I downloaded the 0.7.10 tar.gz from here: [http://code.google.com/p/gnome2-globalmenu/downloads/list](http://code.google.com/p/gnome2-globalmenu/downloads/list)

Wait, you are trying to compile Global Menu yourself even though it is included in Natty 11.04 by default!? Just add "Indicator Applet Appmenu" to the desired panel through its right-click menu, see here for more details:

[http://www.tuxgarage.com/2011/05/disable-enable-global-menu-natty.html](http://www.tuxgarage.com/2011/05/disable-enable-global-menu-natty.html)

Reg. the keyboard shortcut for Slingshot, you can add a shortcut in "System -> Preferences -> Keyboard Shortcuts" for the command "slingshot". But since you can't set single keys there, you need to edit the key combination afterwards in "gconf-editor", the new shortcut would be listed under the path "/desktop/gnome/keybindings/customX". Into the field "binding", enter "Super_L" for the left <Super> key, or "Super_R" for the right one. Although, I would obviously choose another key or key combination for launching just a game. ;-)

Greetings.

---

### Post by Copper Bezel on 2011-09-15
It's crazy, but so far as I can tell, Slingshot the launcher and Slingshot the game take the same command, even though the former comes from the package slingshot-launcher. Sloppy, that. 

Good tip on using gconf editor - I didn't realize you could force a keybinding that way.

---

### Post by Krytarik on 2011-09-15
> **Copper Bezel said:**
> It's crazy, but so far as I can tell, Slingshot the launcher and Slingshot the game take the same command, even though the former comes from the package slingshot-launcher. Sloppy, that.
At least the stated command is still right then. :P

Didn't find a reference to the launcher app upon a quick web search.

---

### Post by Copper Bezel on 2011-09-15
Yeah, it's part of the (thus far little-used) Pantheon desktop shell, from the _[Elementary Team]("https://launchpad.net/~elementaryart")_. It's a splash-screen launcher like Unity's or Gnome Shell's Dash, but at the moment, it's a little limited. It's meant to be used with Wingpanel as a top panel and Plank as a dock. They're all beta software intended for release in a future version of Elementary OS.

---

### Post by Krytarik on 2011-09-15
> **Copper Bezel said:**
> Yeah, it's part of the (thus far little-used) Pantheon desktop shell, from the _[Elementary Team]("https://launchpad.net/%7Eelementaryart")_. [..] They're all beta software intended for release in a future version of Elementary OS.
Ahh, in *this* context I've heard that name once or twice before, I remember now. Thanks for the pointer!

---

### Post by kalebmcc on 2011-09-16
Okay, I got things working as intended thanks to your advice, but after a little usability testing I've decided to revise my designs.

I'm moving the Slingshot shortcut to Docky; is there some way to change the icon? I made a desktop launcher with the desired icon, and it works just fine. However, when I drag it to Docky, it uses the default Slingshot icon. Methinks if I swapped the Slingshot default with the desired icon, it'd work. The problem is, I don't know where to find Slingshot's default icon and Ubuntu's file browser scares me (probably just because I'm not used to it yet).

Secondly, I'm now using the gnome panel applets Window Buttons, Global Menu and Window Title, in that order on the top panel. It works and looks great, except for one hiccup: When I give focus to a non-maximized window, the maximized window in the background's title remains on the panel. Is there some way to only display the window title if the window is maximized AND has focus?

Thanks in advance for helping me out with my questions!

EDIT: Oh, also, is there some way to just draw a vertical line down the middle of the screen, so I can align things better?

---

### Post by Krytarik on 2011-09-16
> **kalebmcc said:**
> I'm moving the Slingshot shortcut to Docky; is there some way to change the icon? I made a desktop launcher with the desired icon, and it works just fine. However, when I drag it to Docky, it uses the default Slingshot icon.
Just copy the .desktop file you created on your desktop to "~/.local/share/applications", this will override the default one then, located in "/usr/share/applications".

> **kalebmcc said:**
> Secondly, I'm now using the gnome panel applets Window Buttons, Global Menu and Window Title, in that order on the top panel. It works and looks great, except for one hiccup: When I give focus to a non-maximized window, the maximized window in the background's title remains on the panel. Is there some way to only display the window title if the window is maximized AND has focus?
Just right-click on the Window Title applet, choose "Preferences", and under "Behavior" enable "Hide when no active maximized windows". ;-)

---

