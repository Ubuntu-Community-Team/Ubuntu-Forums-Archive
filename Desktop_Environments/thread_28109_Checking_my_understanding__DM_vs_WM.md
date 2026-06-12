---
title: "Checking my understanding : DM vs WM"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Wardhog on 2005-04-18
I keep hearing wonderful things about XFCE, and want to try it out.  However, I'm not the only user on my Ubuntu box (currently trying to convert my wife over to Linux, and she is somewhat resistant to change), and don't want to undo all the work I've put into her usage of Ubuntu.  
I want to install and use XFCE only on my own account on the box, not hers.  That's why I want to check my understanding here of what actually constitutes a Gnome desktop.

From what I've been able to gather, the gdm is started by the init process, and is a separate entity from (and required by) the Window Manager. The Gnome Window Manager is started on a per-user basis when they log in.  Do I have this right?

If so, XFCE would be started on a per-user basis as well, just like the Gnome Window Manager, and I would be able to use it with my account only, and not force this change on other users on my system.

Please correct me if I'm wrong.

---

### Post by Klin'Targ on 2005-04-18
This is mostly right. GDM is not required, but is a way to automate the launching of a window manager. If you install XFCE, any user can choose which environment to log into, but the default will likely remain gnome. This means that if a user wants to use XFCE, they can choose to do so, but otherwise they will not notice any changes (gdm will still log into gnome by default).

---

### Post by Wardhog on 2005-04-18
Can a WM run without a DM?

Edit : I think I get it now, does a DM provide a graphical equivalent of logging in as some user and typing startx?  So the answer to my question above is yes.

---

### Post by pdpi on 2005-04-19
[QUOTE=Wardhog]Can a WM run without a DM?

Edit : I think I get it now, does a DM provide a graphical equivalent of logging in as some user and typing startx?  So the answer to my question above is yes.[/QUOTE]
 yep. the answer is yes. And for bonus marks, gnome is full desktop environment, rather than just a window manager. gnome's standard window manager is metacity. There are other programs involved in maintaining a full desktop, like the gnome-pannel.

In fact, you **could** replace metacity with another window manager, and the environment would only change a bit.

This said, many window managers that are designed to work as stand-alones without the benefit of panel applications or that sort of modern appliance supply their own resources to ensure a decent user functionality, like menus and a dock

---

