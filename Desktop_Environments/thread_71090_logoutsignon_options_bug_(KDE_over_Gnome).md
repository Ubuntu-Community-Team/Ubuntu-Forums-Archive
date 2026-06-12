---
title: "logout/signon options bug? (KDE over Gnome)"
date: 2005-10-02
forum: Desktop Environments
---

### Post by dr.drake on 2005-10-02
hmmm, maybe this should have gone here, so this is a copy of my post in the ubuntu forum:

hello.

I first installed Ubuntu with the Gnome desktop, because Gnome lets me edit easier (that way I can use the ubuntuguide), but the lack of costumizability made me install KDE on top of that ( sudo apt-get install kubuntu-desktop ) and all works fine, but...

where, when I log out of gnome, I get the option of 'end current session', 'turn off computer' and 'restart computer', I now only get the 'end current session' option, having me log in to Gnome to be able to shut down my computer from there.

I went to: Control Center -> KDE Components -> Session Manager , and I checked the boxes on 'confirm logout' and 'offer shutdown options', but no succes...
and even when I uncheck that last box box and set the 'default shutdown option' to: turn off computer, when I do logout it still only restarts....

any suggestions?
thanks, eric. (linux newb)

PS,

I read somewhere on this forum that when you have KDE over Gnome and set the default logon to KDE, that it won't give you a "session" option on logon, thus not giving me the option to logon to gnome anymore...
is this true?

( I am trying to install ubuntu at work in the common room, where I want everybody to use KDE as a default, but letting me log on to Gnome to edit and install easier)

thanks again, eric

---

### Post by haaglin on 2005-10-02
You have to use KDM instead of GDM to get this option. In terminal type:

sudo dpkg-reconfigure kdm

And select KDM as default.


Also, KDM do have a session option.

---

### Post by Knome_fan on 2005-10-02
The problem is probably that you are still using gdm, the gnome display manager.
Simply change to kdm with sudo dpkg-reconfigure kdm, then choose kdm and you'll get your logout options in KDE.
Of course you'll either have to reboot or stop gdm and start kdm by hand to see the effect.

About not being able to log into Gnome, I never had this problem and I've been useing KDE/Gnome setups for some time now so I don't think you'll have to worry about this.

---

### Post by dr.drake on 2005-10-02
thanks, it worked!!!
the first 2 times after I applied it (in both KDE and Gnome) I got the KDE logonscreen, couln'd access KDE because it would still default to Gnome.
but after I logged off out of Gnome with Ctrl+Alt+BackSpace it finally worked...

no problem with having one-off sessions in Gnome either.

I'm a happy camper now :)

eric.

---

