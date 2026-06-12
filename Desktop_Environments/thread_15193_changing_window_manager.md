---
title: "changing window manager"
date: 2005-02-12
forum: Desktop Environments
---

### Post by stevetxt on 2005-02-12
Does anyone know how to change the default window manager in Gnome with Ubuntu?  I can't seem to find this information anywhere.  The default wm Metacity seems to cause a problem in which graphics windows open sometimes without the title bar, which is very invoncenient.  I found that others have experienced this problem, and said that it aparently went away when they changed window manager. 

Thanks,

Steve

---

### Post by scoon on 2005-02-12
[QUOTE=stevetxt]Does anyone know how to change the default window manager in Gnome with Ubuntu?  I can't seem to find this information anywhere.  The default wm Metacity seems to cause a problem in which graphics windows open sometimes without the title bar, which is very invoncenient.  I found that others have experienced this problem, and said that it aparently went away when they changed window manager. 

Thanks,

Steve[/QUOTE]

Hey there, 

Different WM's have different procedures for being used w/ gnome or kde.  I used to use openbox ([http://icculus.org/openbox/](http://icculus.org/openbox/)).  It worked well and was fast.  But there are many other options for you to look into. 


scoon

---

### Post by stevetxt on 2005-02-12
I know which one I'll try next - icewm, because I've used it before without problem.  What I need to know is how to the change.  II have not been able to find any how-to or instructions for changing window manager.  

Steve

---

### Post by alastair on 2005-02-12
OK - be careful. I have little Ubuntu/Debian experience, so use at your own risk.

First - install the WM you want i.e. icewm.

Then check the man page for "update-alternatives" i.e.

man update-alternatives

This maintains your desired choice from various options, for various things (e.g. editors, window manager etc.). It looks like you can reconfigure the choice of WM via something like :

sudo update-alternatives --config x-window-manager

Warning - I have not tried this.

---

### Post by mendicant on 2005-02-12
I've changed it on Debian using gnome by doing the following:  copy /usr/share/gnome/default.session to ~/.gnome2/session and edit the gnome-wm line to read something like:
1,RestartCommand=gnome-wm --default-wm <new-wm command> --sm-client-id default1

---

### Post by scoon on 2005-02-12
Hey there, 

Using gconf-editor take a look at desktop->gnome->applications->-window_manager

there are settings to change the default window manager as well. 

scoon

---

### Post by stevetxt on 2005-02-12
Thanks Alastair, Mendicant, and Scoon,

I tried each method, and the only one that worked is the one Mendicant suggested.  It seems that either Gnome or the Ubuntu desktop have made Metacity a very strong default, so that it is hard to change to another window manager, and the methods for changing that appear in the menu or the man page do not work to change it.  

Also, now that I have set icewm as the window manager by that method, it comes up with only the icewm windows and panel after I log in, and the Gnome desktop appears  suddenly a full two minutes later!  

The reason I needed to change is that Metacity seems to have a bug that affects my work very seriously.  From searching on the web I find that others have encountered this same difficulty, and a bug report apparently related to this problem was submitted to Metacity in June 2004.  The problem is that when using applications that produce graphics windows, the windows are sometimes produced without title bars, so they are very hard to move or close.  Changing the window manager in Gnome seems to fix the problem.  I changed to icewm.  Another person changed to Sawfish.  

I would change back to Metacity if this problem was solved in some revision.

Thanks for your thoughts.

Steve

---

