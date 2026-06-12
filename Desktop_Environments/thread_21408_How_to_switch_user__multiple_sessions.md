---
title: "How to switch user / multiple sessions?"
date: 2005-03-22
forum: Desktop Environments
---

### Post by eiden on 2005-03-22
Hi, 

I'm currently a Suse KDE user and now testing Ubuntu, the planned switchover  is next weekend -  one thing remaining which is driving me crazy... 

If I'm logged in, how do you swith user, i.e so that my girlfriend can log in as well and we have two desktops running with the ctrl-alt-F7 / F8 switch?

Ubuntu menus just give me the option to logout from session... this HAS to be obvious, so whip me..

 - Niko

---

### Post by lao_V on 2005-03-22
Are you running Ubuntu under VMWare?
Also, if you want to stay with the KDE then try Kubuntu! Its great!

---

### Post by fjleal on 2005-03-22
[QUOTE=eiden]Hi, 

I'm currently a Suse KDE user and now testing Ubuntu, the planned switchover  is next weekend -  one thing remaining which is driving me crazy... 

If I'm logged in, how do you swith user, i.e so that my girlfriend can log in as well and we have two desktops running with the ctrl-alt-F7 / F8 switch?

Ubuntu menus just give me the option to logout from session... this HAS to be obvious, so whip me..

 - Niko[/QUOTE]
In the command-line, try typing "gdmflexiserver".
If you want your new session inside a window (not full-screen), do: "gdmflexiserver --xnest".

---

### Post by eiden on 2005-03-22
What's VMWare...? No, I have Ubuntu installed to a partition on my backup HD and run it as doubleboot with Suse. The plan is to overwrite Suse with Ubuntu on my main HD. I'm actually starting to like Gnome  ;)

Thanks for the gdmflexiserver hint, I'll try that one tonight.

Niko

---

### Post by fjleal on 2005-03-22
[QUOTE=eiden]
Thanks for the gdmflexiserver hint, I'll try that one tonight.
Niko[/QUOTE]
You're welcome. ;)
You may not have xnest installed - I thing Ubuntu doesn't install it  in its default configuration. If you don't, install "xnest" from the repositories using Synaptic. It's a small package and it's worth it! If you have both Gnome and KDE on the same machine, you can login into your default GUI enviroment (let's say Gnome) full-screen, and also login into KDE in a window as another user (or the same one).

---

### Post by bigzak on 2005-03-22
[QUOTE=eiden]If I'm logged in, how do you swith user, i.e so that my girlfriend can log in as well and we have two desktops running with the ctrl-alt-F7 / F8 switch?

Ubuntu menus just give me the option to logout from session... this HAS to be obvious, so whip me..[/QUOTE]

Applications -> System -> New Login

Jus' like that...

---

### Post by eiden on 2005-03-23
[QUOTE=bigzak]Applications -> System -> New Login

Jus' like that...[/QUOTE]

And there comes the whip... autsch!  ](*,)  I can confirm that all the above  advice works - thanks the responses, you have now a new Ubuntu community member!

Niko

---

### Post by bigzak on 2005-03-23
[QUOTE=eiden]And there comes the whip... autsch!  ](*,)  I can confirm that all the above  advice works - thanks the responses, you have now a new Ubuntu community member![/QUOTE]

Yay! Welcome to the nut house ;)

---

### Post by jazzwhistle on 2006-01-31
Ubuntu breezy and KDE 3.4. Problem launching multiple sessions - gdmflexiserver "or "New Login", same thing, crashdive with 

** Message: Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus
** Message: Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus

Thanks for xnest! Beautiful.  I'd still like to fix the new login problem though - any ideas?

Cheers

---

### Post by jazzwhistle on 2006-02-01
Just upgraded to KDE 3.5, and I've got a new menu item "Switch User".  But it doesn't work either. I get so close to a new login screen, millions of black and white pixels and a pretty hourglass for 30 seconds, and then I get kicked back in to this session. Same message as above about that devil D-BUS.

I found this info:

> Are you sure that the daemon is actually running?  My guess is
that the daemon died because of some weirdness in your session.conf (in
particular having two <listen> directives looks wrong).

For what it's worth, I don't use a custom .conf file.  Instead I do
debugging like this:

In one terminal, run:

DBUS_VERBOSE=1 dbus-daemon --session --print-address

That will print an address like this (along with other debug goo):

unix:abstract=/tmp/dbus-hBeFb6bmsV

Then in another terminal, do:

export DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-hBeFb6bmsV

And now I no longer ger D-BUS errors, instead I get: * Message: Screensaver is not running!

Getting there slowly...

---

