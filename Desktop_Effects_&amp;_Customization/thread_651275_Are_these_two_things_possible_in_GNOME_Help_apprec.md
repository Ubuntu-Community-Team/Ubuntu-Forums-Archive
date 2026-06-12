---
title: "Are these two things possible in GNOME? Help appreciated."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by Gigamo on 2007-12-27
Hello.

I would like to know if these 2 things I've been thinking about are possible in GNOME :)

1. The GNOME panel. I have it set so that it isn't expanded over the entire screen as you can see in the desktop pic I attached. But what annoys me, is that everytime I open a new application or window, the panel automatically resizes to accomodate that new window (in the window list). That alone isn't the problem, the problem is that it takes the panel more than a second to actually resize, and it can't be used while it does. 
So my question: Is it possible to give the panel a fixed width, and have the window list resize the window buttons instead of having the whole panel resizing, like in XFCE?

2. The rightclick menu! Yes :). Is it possible to have a rightclick menu to open apps with, like in openbox/fluxbox/xfce/whatever! :)? The only thing I have found so far is how to add an 'open terminal' option to it. 
I am hereby also wondering, and this would be another option, if it is possible to start gnome with the option "nautilus --no-desktop" to have it use the rightclick menu from Openbox or something the like? If so, how?

Thanks!

---

### Post by raul_ on 2007-12-27
About 1)

It is possible, maybe you have "panel resizing" option enabled? Or something like that, i haven't used gnome in an year.

2) I think it's possible if you dump Metacity as your window manager and use something like openbox, but i'm not sure about that, i'm not a *box guru.

---

### Post by Gigamo on 2007-12-27
Sadly, I don't see any panel resizing option in the panel properties :(

I have been thinking about openbox as well. The problem is, when I select GNOME/Openbox as my session, i just get my default gnome desktop with no openbox rightclick menu or openbox window decoration.

---

### Post by walkerk on 2007-12-27
If you run Openbox over Gnome you will not get the right click menu. You need to press Ctrl-Alt-Backspace and log back into an Openbox session.

If you want the feel of Gnome with a right click menu I suggest you try out XFCE.

I'm a full time Openbox user and I love it. If you want Compiz *box is not for you...

---

### Post by walkerk on 2007-12-27
for the expand option... right click the panel and goto preferences and un-check the Expand check-box

---

### Post by Gigamo on 2007-12-27
> **walkerk said:**
> If you run Openbox over Gnome you will not get the right click menu. You need to press Ctrl-Alt-Backspace and log back into an Openbox session.

If you want the feel of Gnome with a right click menu I suggest you try out XFCE.

I'm a full time Openbox user and I love it. If you want Compiz *box is not for you...

Nah I'm not really into compiz. Also, I would like to stick with gnome.

Isn't it possible to set the GNOME/Openbox session to run nautilus --no-desktop instead of nautilus? Or to only use the gnome panels and nothing else?

Sorry for being a bit stubborn ^^

[QUOTE=walkerk]for the expand option... right click the panel and goto preferences and un-check the Expand check-box[/QUOTE]

This is the option that manages the panel to be stretched over the entire bottom, or to be only as wide as it needs to be. If it is checked it will stretch over the entire width, unchecked is like on my screenshot.

---

### Post by raul_ on 2007-12-27
If you want Gnome to be so XFCEish, why stick with it? Do you have any strong motives?

---

### Post by jken146 on 2007-12-27
For the gnome --no-desktop thing, have a poke around in gconf-editor.

---

### Post by Gigamo on 2007-12-27
> **raul_ said:**
> If you want Gnome to be so XFCEish, why stick with it? Do you have any strong motives?

Because I have no experience at all with XFCE and configuring it to my liking would take centuries :D

---

### Post by walkerk on 2007-12-27
> **Gigamo said:**
> Because I have no experience at all with XFCE and configuring it to my liking would take centuries :D

XFCE configuration is pretty straightforward.. similar to Gnome.

Oh, and I misread your #1 :) XFCE can set an exact pixel size for the xfce4-panel

---

### Post by urukrama on 2007-12-27
You can run easily run Gnome in Openbox. Install the latest version (use apt/Synaptic if you are running Gutsy, use the deb on the [openbox site]("http://icculus.org/openbox/index.php/Main_Page") (currently down) or compile from source if you run an earlier Ubuntu (see [here]("http://urukrama.wordpress.com/openbox-guide/") for details)). 

To have Openbox' right click menu in Gnome you'll have to disable Nautilus from drawing the desktop. Kill it in the Gnome sessions (under System > Preferences > Sessions), but make sure it is set to Normal (and not Restart or Refresh, or whatever it is called) or it will restart automatically. Use Nautilus with the following command to have only the file manager:

> nautilus --browser --no-desktop

To edit the Openbox menu, you can use [obmenu]("http://obmenu.sourceforge.net/") (not in the repos).

You might find it easier to just use Xfce, though. Try it out and see what you like best. Xfce will allow you to have a right click desktop menu and icons on the desktop (Openbox doesn't have icons on the desktop), icons in the menus, an automatically updated menu (when you install new applications) and compositing. It isn't very hard to configure (perhaps even easier than Openbox). If you want to install it, I suggest installing the package xfce4 rather than xubuntu-desktop, as I find it much faster and it comes with less additional applications (like Abiword, etc.)

EDIT: To see how you can have a right click menu in Gnome (either through a different window manager or by extending the Nautilus menu/actions) have a look [here]("http://ubuntuforums.org/showpost.php?p=3678683&postcount=12").

EDIT2: btw, what Gtk and Metacity theme are you using in that screenshot?

---

### Post by Gigamo on 2007-12-27
That would be Murrine DuoClean GTK2 theme and uel-Calla emerald theme. Thanks for the links :)

---

### Post by urukrama on 2007-12-27
Thank you.

---

### Post by jviscosi on 2007-12-27
If you install XFCE, I believe that you can get the XFCE right-click menu in Gnome or anywhere else just by running xfdesktop (or it might be xfdesktop4, I don't remember exactly) without actually having to start an XFCE session.  I think, but am not 100% sure, that this will take over your desktop wallpaper, icons, etc.  Also, you'll want to use the XFCE settings app to configure the menu contents.

I'd go along with the others who've suggested giving full-blown XFCE a try to see if you like it.  It's fast, pretty, and quite easy to set up.

---

### Post by Phristen on 2007-12-28
Sorry for noob question (and for off-topic), but what is that panel at the right upper corner on your screenshot? Some sort of screenlets?

---

### Post by urukrama on 2007-12-28
> **Phristen said:**
> Sorry for noob question (and for off-topic), but what is that panel at the right upper corner on your screenshot? Some sort of screenlets?

That is conky. It is in the repos. See [this]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") thread for configuration options.

---

