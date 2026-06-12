---
title: "Don't even know how to title this question."
date: 2010-06-28
forum: Desktop Environments
---

### Post by pepsifx357 on 2010-06-28
I have an idea and I want to know if anybody knows how to do it.

I would like a desktop like enlightenment 16, you know the one with the white background, not the new one.  However, I would like for the background to be the black terminal.  Nothing but terminal.  No borders, no button, no task bars or anything.  I want it to look like your running Ubuntu without X.

When I execute a program using the terminal, then the normal window appears.  When you execute firefox, it would show up with it's window borders and everything.  Then when I exit, you would only see that black terminal background.

How could I do this, do you see unforeseen problems with this, and do I need to elaborate more?  

Edit:  To add to this, I like nautilus, I think it's a very good file manager from what I have seen.  So maybe I could keep nautilus but still have the terminal background?

Thanks,

Ben

---

### Post by BenAshton24 on 2010-06-28
This sounds like a really interesting idea :D

Ok so step one, I guess, is to remove all of your panels. You can do this by opening "gconf-editor" and navigating to /aps/panel and in the "general" key, emptying "toplevel_id_list". Next you want to put a terminal on your desktop. There is a tutorial here: [http://ubuntuforums.org/showthread.php?t=202249](http://ubuntuforums.org/showthread.php?t=202249) but it's a bit out dated so you may have to google for something more recent. Either way it shouldn't be too difficult.

Hope this helps,
Ben.

---

### Post by jpkotta on 2010-06-28
It sounds like you might want a tiling window manager.  There are many: [http://en.wikipedia.org/wiki/Tiling_window_manager](http://en.wikipedia.org/wiki/Tiling_window_manager).

I did the terminal as a background thing years ago.  What I do now is have a pair of terminals that can be hidden or shown with keybinds, and I have them set to always be on top of any other windows.  This way I always have easily accessible terminals, and they never get in the way.  I found that having two is much better than one because often I need to run an auxiliary command (e.g. bring up a man page while typing in a command line).  Yakuake is somewhat similar to my set up.  

If you want to continue using Nautilus, you need to launch Nautilus with the --no-desktop option, otherwise it takes over the background.

---

### Post by Python Jedi on 2010-06-28
On nautilus, you can disable it from drawing the desktop with gTweakUI.  I used it to let compiz draw the desktops, but you could use it here as well.  You can use synaptic (System>Administration>Synaptic Package Manager) or a terminal command ```
sudo apt-get install gtweakui
```  You can then go into System>Prefrences>gTweakUI-Nautilus (there will be others, feel free to play with 'em)  and disable drawing the desktop.  You can also do what jpkotta said, I trust that they would know where to edit the command.  Your idea sounds interesting, I might have to try it sometime.

---

### Post by pepsifx357 on 2010-06-29
> **Python Jedi said:**
> On nautilus, you can disable it from drawing the desktop with gTweakUI.  I used it to let compiz draw the desktops, but you could use it here as well.  You can use synaptic (System>Administration>Synaptic Package Manager) or a terminal command ```
sudo apt-get install gtweakui
```  You can then go into System>Prefrences>gTweakUI-Nautilus (there will be others, feel free to play with 'em)  and disable drawing the desktop.  You can also do what jpkotta said, I trust that they would know where to edit the command.  Your idea sounds interesting, I might have to try it sometime.

I've never seen compiz draw the desktop.  Is there any advantages?

---

