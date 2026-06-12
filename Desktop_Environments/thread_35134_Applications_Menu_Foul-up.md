---
title: "Applications Menu Foul-up"
date: 2005-05-17
forum: Desktop Environments
---

### Post by AndEat on 2005-05-17
Under the applications destop bar I now have an entry labeled Debian that opens to more folders, which opens to more folders...I want to get rid of this as this is unecessary duplication. There is also alot of programs I don't remember enabling. 

I suspect this ocurred after following the directions here:

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#ubm](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#ubm)

Though I am not certain...I haven't even gotten to play with the newly installed boot manager.

I tried editing /usr/shared/desktop-directories to no effect.

I am trying to figure what happened exactly and how to fix it. 

How do I edit menus? Any tips on how to clean this up?

---

### Post by AndEat on 2005-05-17
As an aside, I now am having trouble with ctrl-alt-backspace rebooting GNOME. I don't know if this is related....

---

### Post by AndEat on 2005-05-20
A certain sign of madness a la Arctor I'll reply to myself.....

I think the problem in part is related to enabling backports. I don't quite understand the the fine details of the the update manager although I am learning. Where would you look to find where this info about the menu is stored and what it is connected to to disable and/or clean up? 

This could something outside of my current range of knowledge, so keep looking. And  watch the spelling and grammar while your at kid.




hmmmmmm

---

### Post by Fass on 2005-05-21
I don't really understand your problem, but could [this be of service](http://www.realistanew.com/projects/smeg/)?

---

### Post by AndEat on 2005-05-28
Thanks--I had tried that app, but for some reason what I was looking for was on the menu but could not be manipulated in the program. 

I was able to fix the problem eventually by backtracking my installed packages though.

---

### Post by oritpro on 2005-05-28
I am in the same boat as you are and find it really amazing that a full featured menu editor doesn't exist for Gnome.

You can create menu entries but can't get rid of them. 

I am also curious as to why Ubuntu, for all it's strengths, ships with Gnome as the default window manager.  KDE has been and still is superior to Gnome, and that's just my opinion.

Of course one can always install KDE but I already have several hours into the current install fixing the various quirks and customizing it to my liking. There is only one way that I know of to delete application menu items and that is to delete it from /usr/share/applications but you can't delete folders that way.

---

### Post by Markrian on 2005-05-29
The Debian menu item in the Applications menu comes from the package called *menu* - it's a pacakge developed by the debian people to bring a unified menu architecture to all the various window managers available out there. With FreeDesktop's menu specification, however, menu is somewhat obsolete.

I imagine that some backported packages you installed pulled in menu with it. Removing menu (and associated packages) should 'fix' the problem.

As for menu editing, GNOME had a menu editor, of sorts, in previous versions. They removed that and some other functionality in GNOME 2.10 (what Hoary uses), but didn't replace it with anything. GNOME 2.12 will fix this along lots of other things.

In the mean time, search the forums for something called *smeg*, Simple Menu Editor for Gnome. I believe that is what will be included in GNOME 2.12, though it's available and works now.

Each to their own! I prefer GNOME to KDE, though it used to be the other way around. Now I find GNOME's simple interface far more useful. KDE is too configurable - the fact that you've already spent hours configuring it demonstrates that, I think.

I think you'll find that GNOME has greater corporate backing than KDE as well, such as from Sun, Novell, Nokia and others. KDE (it seems to me) only has linux vendors like Mandriva and Lindows, which don't contribute much.

Just my opinion, of course. Point is, there is a choice. Some people prefer GNOME, and for them Ubuntu is perfect. Others prefer KDE, and they have Kubuntu.

---

### Post by oritpro on 2005-05-29
I do have SMEG installed but unless I am missing something, it doesn't support menu editing and deletion.

After spending a couple hours grepping around the system and reading up on the latest Gnome menu specification, I was able to locate the menu files and manually delete one undesirable entry but the Debian menu that was created by following the instructions here: 

[http://www.frankandjacq.com/ubuntug.../index.html#ubm](http://www.frankandjacq.com/ubuntug.../index.html#ubm)

still persists even though that entry was deleted from all menu files as well. These files are located in /etc/xdg/menus, HOME/.config/menus and /usr/share/gnome-app-install.

For what it's worth, I do prefer the clean and organized look of Gnome over KDE, but when it comes to flexibility, KDE seems to be better.

---

### Post by oritpro on 2005-05-29
*** UPDATE ***

Ok, found and fixed it (finally!).

In addition to deleting the Debian menu entry in the applications.menu files found in the locations mentioned previously, the was a desktop file located in home/.local/share/applications called Add New Entry.  The actual filename was 1117302142.desktop.  The contents were:

[Desktop Entry]
Comment=
Name=Add new entry...
Exec=
Encoding=UTF-8
Terminal=false
Type=Application
Categories=Application;Debian;
Icon=

The Categories field specifies that this entry goes under the Debian submenu in Applications so that is why it persisted despite deleting the Debian submenu from the menu files.

Deleting this file fixed the problem.  \\:D/

---

