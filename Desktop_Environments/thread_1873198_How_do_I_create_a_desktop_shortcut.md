---
title: "How do I create a desktop shortcut?"
date: 2011-11-01
forum: Desktop Environments
---

### Post by ausairman on 2011-11-01
Hi Everyone,
I want to create a shortcut/launcher to programs or directories on the desktop, but can't seem to work out how to do this. I'm using unity on ubuntu 11.10...
Arman

---

### Post by mcduck on 2011-11-01
Use the "Main Menu"-tool to create the launcher. It will then appear in the Dash, and you can drag it from there to your desktop.

For directories you might want to just use a symbolic link instead, easily created by drag&dropping the directory to desktop using middle mouse button, and then selecting "Link Here" from the popup menu.

---

### Post by Mark Phelps on 2011-11-01
> **mcduck said:**
> Use the "Main Menu"-tool to create the launcher. It will then appear in the Dash, and you can drag it from there to your desktop.

OK ... so is this intended to serve as the replacement for the 11.04 option of right-clicking on the desktop and choosing Create Launcher?

---

### Post by mcduck on 2011-11-01
> **Mark Phelps said:**
> OK ... so is this intended to serve as the replacement for the 11.04 option of right-clicking on the desktop and choosing Create Launcher?

No, it's the same tool that was used for creating launchers and managing the Applications menu in all previous Gnome versions.

For some reason or other Gnome developers removed the option to create launchers directly from the right-click menu in Nautilus, so the Main Menu tool is currently the best one available for the purpose.

If you want to have the option in your right-click menu, you could create empty .desktop file template into ~/Templates. That would allow you to create an empty launcher from the right-click menu, then right-click the new launcher, go to Properties and set the name, command, icon etc. for the launcher there.

---

### Post by Mark Phelps on 2011-11-01
Thanks mcduck ... I'll have to give this a try.

---

### Post by randywilharm on 2011-11-01
> **mcduck said:**
> Use the "Main Menu"-tool to create the launcher. It will then appear in the Dash, and you can drag it from there to your desktop.

For directories you might want to just use a symbolic link instead, easily created by drag&dropping the directory to desktop using middle mouse button, and then selecting "Link Here" from the popup menu.



[COLOR="Blue"][SIZE="3"]I Thank You for that...I just learned something...[/SIZE][/COLOR]

---

### Post by ausairman on 2011-11-01
> **mcduck said:**
> Use the "Main Menu"-tool to create the launcher. It will then appear in the Dash, and you can drag it from there to your desktop.

For directories you might want to just use a symbolic link instead, easily created by drag&dropping the directory to desktop using middle mouse button, and then selecting "Link Here" from the popup menu.

Thanks, this would be great, but I don't know how to access this tool. I'm using the standard ubuntu unity interface and I can't see the "Main Menu" tool anywhere. I've tried dragging objects from the dash (I'm assuming you mean the "Dash" feature at the top of the unity bar) onto the desktop but they just bounce right back into the unity bar...

---

### Post by Mark Phelps on 2011-11-01
Me to. ... I typed Main Menu in Dash ... and it finds NOTHING.

So, is this yet ANOTHER regression from 11.04 -- a feature in Natty that is no longer in 11.10?

UPDATE: I'm in Natty and, like with the desktop Create Launcher function, this is ANOTHER Feature that they took AWAY from us for 11.10!  Entering Main Menu in Dash in 11.04 does indeed display a panel; in 11.10, it does NOTHING.

You know, it's taking things away from folks that drives them away!

---

### Post by ausairman on 2011-11-02
Ok so I found the "Main Menu" tool by clicking on the dash button, then on the little applications button at the bottom, then searching for it. Then I added a launcher, which I added to the "Science" submenu, in my case called "Pointwise". 2 questions:

1) Why can I still not search for it from my dashboard and thus add it to the unity bar or my desktop?

2) What is the purpose of the main menu and all that whole menu tree when everything is amalgamated into unity?

---

### Post by Mark Phelps on 2011-11-02
IN my case, that found a package that COULD be installed.  It wasn't already installed on my system.

But ... I took the larger route and installed alacarte instead.  That got me Main Menu and Gnome Panel and other stuff I missed.

That's one of the great things that keeps me coming back to Linux -- if it's not readily visible, there's always a way to add it from behind the scenes!

---

### Post by ausairman on 2011-11-02
Would really appreciate if someone could give me a way to create a launcher on my desktop, that works with unity in 11.10... I realise there are round-about hacks that may or may not work, but there must be a way to launch a command from an icon on the desktop, surely...

---

### Post by ausairman on 2011-11-02
I found a link here that seems to illustrate a painful way of doing it: [http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/](http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/)

If this is the only way to create a desktop icon in ubuntu then I'm extremely disappointed in the makers of the new unity setup...

---

### Post by stinkeye on 2011-11-03
> **ausairman said:**
> I found a link here that seems to illustrate a painful way of doing it: [http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/](http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/)

If this is the only way to create a desktop icon in ubuntu then I'm extremely disappointed in the makers of the new unity setup...

In addition to that link you can
save this script as **Create_Desktop_launcher** for a right click nautilus script item.
```
#!/bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new
```
Place in ~/.gnome2/nautilus-scripts/ and make executable.

PS: It's more to do with the transition from gnome2 to gnome3 than Unity.

---

### Post by ausairman on 2011-11-06
Thanks, I'll give that a try!

So is this a feature that will be reimplemented soon or has it been deliberately removed?

---

### Post by mcduck on 2011-11-07
> **ausairman said:**
> Thanks, I'll give that a try!

So is this a feature that will be reimplemented soon or has it been deliberately removed?

More likely it's been deliberately removed, as Gnome 3 doesn't even use desktop icons, let alone desktop launchers, by default. Without desktop launchers there's not much reason for Gnome to add a tool for creating desktop launchers.

Perhaps Ubuntu developers, or somebody else, creates a new tool for the purpose. But currently you already get pretty close using any of the workarounds mentioned in this thread.

---

### Post by ausairman on 2011-11-09
>  			 		 	 	 In addition to that link you can
save this script as **Create_Desktop_launcher** for a right click nautilus script item.

When I did that, it appeared in the scripts dialog but when I clicked on it nothing happened... Does this mean that it's impossible to create shortcuts to things in 11.10? I'm finding my 11.10 experience so far to be very frustrating...

---

### Post by stinkeye on 2011-11-10
> **ausairman said:**
> When I did that, it appeared in the scripts dialog but when I clicked on it nothing happened... Does this mean that it's impossible to create shortcuts to things in 11.10? I'm finding my 11.10 experience so far to be very frustrating...
Did you give the script executable permissions?
Right click properties > permissions
Did you install gnome-panel?

---

### Post by Mark Phelps on 2011-11-10
The link below is to a tutorial on how to create launchers -- but it covers much the same things you've already done:

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html]("http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html")

---

