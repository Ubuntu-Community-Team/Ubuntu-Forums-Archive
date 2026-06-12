---
title: "Help, Injured My Laptop w/ Desktop Effects"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by MimeyNaomi on 2008-01-22
Or SOMETHING.

Here is the end result: I can boot up, I get the splash screen and login window, I log in, and then one of three things happens:
~ I get my desktop image but no desktop icons, no panel, no dock, right-clicking does nothing;
~ OR, I get my desktop with no panel or dock, but the two items on my desktop are there, and I can open one of them (an OpenOffice doc) but can't open Nautilus from there, I can right click and open the window to create a launcher, and that's about it;
~ OR, I see my desktop flash before my eyes several times, I see my panel and an error message I can't make out, then it quits and I'm left with the empty desktop.  Fortunately, hitting my power button still pulls up the shutdown menu, so I've been able to safely shut down every time, but other than that it seems frozen.

What I did that day:  in an effort to imitate OS X, I installed Screenlets, Compiz Fusion (for the widget layer), Beryl (for the OS X-style Emerald theme), and Avant Window Navigator (for the dock).  Everything was going fine until I decided to install the macmenu applet (found directions for Feisty somewhere on this forum, I'm using Gutsy but tried it anyway).  Rebooted, and this weird crap started up.

What did I do, and how can I fix it?  Please, if you have any clue, give me a sign.  I'm helpless.

---

### Post by MimeyNaomi on 2008-01-22
Update:

I just booted up for the first time since Sunday, and got an error message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include:  the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

In addition to this, my top panel appeared briefly before disappearing, and the folder and OpenOffice doc on my desktop are there.  I can open the document, but when I try to open the folder, the icons disappear and Nautilus doesn't start.  My desktop effects seem to be working.

---

### Post by rfs13286 on 2008-01-22
Hello
Due to my limited experience I cannot help in solving the underlying problem that you have. However, maybe you can try this procedure to disable compiz and use metacity to at least have a functional desktop while you wait on a more experienced helper.

I don't know if this works for you but try to press Alt+F2 to bring up the run.. dialog and then type: 

```
metacity --replace
```

This will disable compiz and enable metacity, which is GNOMEs default window manager (doesn't have fancy effects though). After that your normal desktop should be back, hopefully.

Cheers

---

### Post by MimeyNaomi on 2008-01-22
Thanks very much for replying.  Unfortunately Alt+F2 wouldn't bring up the run dialog.  I booted in recovery mode and tried "metacity --replace" but got "Window manager error:  unable to open X display."  Rebooted, nothing had changed.

---

### Post by rune0077 on 2008-01-22
You shouldn't run beryl and compiz at the same time, I think. If you have a full install of Gutsy, compiz-fusin is already installed by default, and since that is actually a merge between compiz and beryl, you may have three different windows managers on your system now. 

Try to boot up in safe mode. That should give you a desktop without all the fancy stuuf. Then uninstall beryl and compiz (actually, Synaptic calls compiz-fusion for compiz, so you may want to keep that). Make sure you have the compizconfig-settings-manager installed. Finally install Emerald (you don't need Beryl, it'll run on compiz-fusion).

---

### Post by MimeyNaomi on 2008-01-22
My bad, I was unclear--I didn't install Beryl on top of Compiz-Fusion, just Emerald themes.  Thanks for the suggestion.  I'm pretty sure now that what broke GNOME was the macmenu-applet; that plus Avant Window Manager are the two things I installed before things went awry.  Before then, with Compiz-Fusion enabled and Emerald themes installed, I'd rebooted just fine.

Right now I'm trying to find a way to uninstall macmenu-applet but am having difficulties.  Anyone?

---

### Post by jesusfreak107 on 2008-01-22
I did the same thing, but with a different 3D program (the one that switches your desks in 3D). start in recovery mode, and type "sudo apt-get remove *(nameofpackage)*

---

### Post by Samhain13 on 2008-01-22
While you're in the login screen even if you're not in Recovery Mode, hit Ctrl + Alt + F1. Log in from there and follow JesusFreak's instruction on uninstalling. Then restart:

```
sudo reboot
```

---

### Post by MimeyNaomi on 2008-01-22
YES!  I managed to uninstall macmenu-applet and it rebooted fine.  Glad to know it was just that, and not any of my other eyecandy.

Thanks, Samhain and JesusFreak.

---

