---
title: "deskbar as applet in openbox?"
date: 2007-12-16
forum: Desktop Environments
---

### Post by crazybilly on 2007-12-16
I'm working on setting up Openbox as an alternate light desktop enviroment when I don't feel like booting into Gnome. I've got gnome-volume-manager and nm-applet running, a taskbar (pypanel).  

I don't have my menus set up (obmenu is giving me fits about a nonexistent debian menu), but rather than fight that battle, I'd rather just use deskbar for launching everything.  The problem is that the deskbar applet doesn't run very well in Openbox.  

First of all, when I launch it in Openbox, rather than running as an applet in pypanel's system tray, it launches as its own window.  I have a suspicion I can fix that with some window manager text file configuration trickery. I don't know how yet, but I think I can figure it out.

What I can't figure out is that when I activate deskbar w/ my shortcut, while it opens the input bar just fine, it doesn't give it focus.  This is a problem in Openbox by itself and in Gnome/Openbox (using ob as the window manager in gnome). 

Has anybody worked through this?  And how?  

I'd love to understand the problem and embiggen my brain about it....Thanks!

---

### Post by bonzodog on 2007-12-16
Firstly, sort out your openbox menus.

You need to install the debian menu package for obmenu to work. It's there in synaptic. Open synaptic from a terminal if needs be using ```
sudo synaptic
```

Also, there is a handy little script called menumaker available from sourceforge, which will build an openbox menu for you.

---

### Post by crazybilly on 2007-12-16
Well, since I installed kubuntu-desktop, I've already got too much crap in my menus...I'm hoping to avoid having other stuff to remove.

Will installing the debian menu package affect how the deskbar applet runs?

---

### Post by crazybilly on 2007-12-16
my other motivation to get the deskbar thing straightened out is so I can use Gnome/openbox with deskbar.  Right now, the hotkey only opens the applet.  then I have to click into it (like I do in openbox by itself), which kind of defeats the purpose of having a keyboard shortcut....

---

### Post by urukrama on 2007-12-17
I don't think you can run deskbar in pypanel (or fbpanel or lxpanel). You could use gnome-panel with the deskbar in Openbox, though (just add 'gnome-panel &' to your autostart file).

If you need help with menus, use menumaker and have a look at [my guide]("http://urukrama.wordpress.com/openbox-guide/") how to do so.

---

### Post by crazybilly on 2007-12-18
too bad--I was really liking pypanel.  How does gnome-panel compare to pypanel as far as resources used?

Obviously, I'm kind of shooting myself in the foot using deskbar on a minimal install...at work I use windows + launchy and only touch the start menu or even much of explorer b/c Launchy does everything I need.  I'm hoping for something really similar w/ Openbox+deskbar, really. Katapult is tied too much to kde and just doesn't do what I want the way I think it should (I can't navigate the directory tree structure by hitting tab like I can w/ Launchy).

But am curious about gnome-panel. Pypanel is cool, if only b/c it's so simple, but seems to do just about everything I want (although I did like having the ubuntu start button to remind what I had available).

I suppose I'll give it a go.

Anything else Launchy-like I could try out beside deskbar and katapult?

---

### Post by crazybilly on 2007-12-18
using gnome-panel isn't bad, really.  But I'm still having troubles with the deskbar text field getting focus when I activate deskbar...any thoughts?

---

### Post by urukrama on 2007-12-18
Gnome-panel uses a bit more resources than pypanel, but you also get more (applets, menus, etc.) than with pypanel. Alternatively, you could try to use the xfce4-panel with deskbar (using [this]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin")); I'm not sure if it works, but it might be worth a shot.

What do you use deskbar for, actually? If it is just to launch applications, perhaps you could use something like gmrun (similar to Alt+F2 in Gnome and KDE). It is in the repos.

---

### Post by crazybilly on 2007-12-18
At work I use Launchy.  And I use it to open just about everything.  

The best feature is its file tree navigation:  if you want to open a folder buried somewhere, but can't remember the name or the exact location, you can start typing the file address.  It autocompletes for you, and gives you options.  

You can tab to move to the next thing.  When launching programs, you can tab to pass commands to them.  

Last night, I tried gnome do and gnome launch box.  They both were rather unintuitive, did a bad a job at searching (they got confused when I typed 'home' and wanted to go to Ubuntu Home Website, and wouldn't give me a way to change it to my home directory). I was as unimpressed with them as I was with Katapult.

I did some looking--it turns out that a new version of Launchy is about to come out, this one built on QT, so it'll be cross-platform. The development process seems to be churning along, so I think I'm just going to wait till the day arrives....

I suppose this means I need to sort out my menus, hehehe.

---

