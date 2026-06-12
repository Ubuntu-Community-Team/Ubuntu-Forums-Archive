---
title: "Vertical dock/panel options for xfce"
date: 2010-02-12
forum: Desktop Environments
---

### Post by awdyson on 2010-02-12
I'd love to have my dock oriented vertically on the side of the screen.
The problem is that the native dock renders the task bar horribly that way.

Cairo-dock has trouble with the system tray.
In the dock, the icon needs to be clicked, and it's annoying as hell as a desklet.

Alltray doesn't function properly in xfce.

Docky would call for Gnome libraries (I think).

AWN doesn't have an option to attach to the side of a screen.

Also, I've had trouble finding options in the alternative docks for the organization of applets/launchers.
I like the native panel because it'll pull the xubuntu menu to the top and leave the systray and any applets on the bottom.

Any suggestions?
If I could make the taskbar look proper or have all open applications show up in the task bar I'd be happy.

Thanks in advance guys.
Cheers
Alex

---

### Post by ajventi on 2010-02-19
Sounds like most of this is just the way Xfce is, not much you can do about it other than code diving.

The only thing I could suggest is running gnome-panel in Xfce

I just tried it myself, Press Alt-F2 and run gnome-panel 

If you have the Xfce session-manager and save the session before you log out it should keep the gnome-panel all the time for you.

---

### Post by Hero of Time on 2010-02-20
> **ajventi said:**
> Sounds like most of this is just the way Xfce is, not much you can do about it other than code diving.

The only thing I could suggest is running gnome-panel in Xfce

I just tried it myself, Press Alt-F2 and run gnome-panel 

If you have the Xfce session-manager and save the session before you log out it should keep the gnome-panel all the time for you.
He isn't talking about the panel that comes with the installation by default, Xfce can park it's panel to the side of the screen too. He's referring to those app docks that Mac OSX has at the bottom. It's very obvious because there is no reference to panels, only docks and applications that provide that dock (AWN, Cairo, etc).

---

### Post by ajventi on 2010-02-20
> **Hero of Time said:**
> He isn't talking about the panel that comes with the installation by default, Xfce can park it's panel to the side of the screen too. He's referring to those app docks that Mac OSX has at the bottom. It's very obvious because there is no reference to panels, only docks and applications that provide that dock (AWN, Cairo, etc).

Oh I must have misunderstood him when he talked about the Xfce panel and the features he liked about it, my apologies.

---

### Post by Jose Catre-Vandis on 2010-02-20
Try wbar, coupled with wbarconf

---

### Post by denham2010 on 2010-02-20
> **awdyson said:**
> 
AWN doesn't have an option to attach to the side of a screen.


Try installing the Awn PPA. [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

This is much more recent than the version in the repositories, and supports side orientation.

---

### Post by awdyson on 2010-03-01
> **denham2010 said:**
> Try installing the Awn PPA. [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

This is much more recent than the version in the repositories, and supports side orientation.

Thank you very much.
It's funny, I gave up on AWN because I read on their wiki that they had no interest in incorporating this functionality.
Must have been an old entry.

---

### Post by koleoptero on 2010-03-01
Also the native one works fine vertically, but some GTK themes use images or horizontal gradients as the background of the panel, so when you put it vertically it looks like sh**. Use the default albatross theme and put the xfce panel to the side, then instead of the task list use the iconbox applet to show only icons and you'll see the difference. ;)

If you want to get rid of the default background for the panel in other themes, you have to go to ~/themes/THEME_NAME/gtk-2.0/ open the gtkrc file and find the part of it that applies the background to the panel (it shouldn't be as hard to find as it looks at first), and then comment out those lines (put # in front of them).

[See here what I mean.]("http://www.flickr.com/photos/44514586@N07/4225968476/")

---

