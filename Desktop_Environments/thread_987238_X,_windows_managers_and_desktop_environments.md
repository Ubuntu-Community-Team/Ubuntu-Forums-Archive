---
title: "X, windows managers and desktop environments"
date: 2008-11-19
forum: Desktop Environments
---

### Post by Tony Williams on 2008-11-19
I have read up however I am still puzzled on the subject.  I am a bit of a newcomer (sorry) I would like to futher understand this.

What is the major difference between X, windows managers (IceWM, etc) and the desktop environments (KDE, GNOME).  What do they control and are they all interchangable, how do they interact with each other?

How does one go about swapping KDE or GNOME or vice versa and what difference does it make using a different WM on the same desktop environment?

What are sessions?  and what happenes if I start a new one, is it like a second login on a different account. or the same account and can you log in with one session and another on multiple displays?

I'm trying to cram in some info on this ... like I said, currently confused on it.

Anyhelp is great.

---

### Post by win4thebin on 2008-11-19
X is well the base and window managers are the way x opens windows and the like. there is absolutely no difference between a window manager and desktop environment as they are the same thing.

---

### Post by win4thebin on 2008-11-19
A session is the desktop environment you select to log in and use. if you want to add xfce to ubuntu open terminal and type: *sudo apt-get install xfce-desktop* or *sudo apt-get install xubuntu-desktop*.

---

### Post by snova on 2008-11-19
Ok, interesting subject...

X is a server that controls the display. All graphics ultimately go through X.

The Display Manager is the program that is run first (or something like that). It asks you for your password and permits you a login.

A Window Manager is responsible for the borders around windows, as well as the titlebar. Without a running WM, it's about impossible to do anything, not even so much as to resize/move a window. Try killing Metacity (or Kwin for KDE) if you want to see what life is like without one (it's awful).

A Desktop Environment is really just a collection of programs. Several of them running together work to procure you a useable GUI. For Gnome, for example, there is a program controlling the panels, a program controlling the background, and so on, whereas KDE has similar (in functionality, that is) but different programs. Gnome and KDE both include their own window manager.

They interact quite well, there is no reason why you can't run one DE with your favorite applications from another.

A session... not completely sure. It seems to have two meanings. When logging in, it applies to which desktop environment you wish to start (there's a menu). When logged in, I think it's essentially a set of running programs along with their state, so that you can logout and log back in again and have everything the way it was before.

If you want to try KDE, just install the "kde" package. The "kubuntu-desktop" package depends on KDE but also a few other things, one of which is branding...

There is also XFCE, which is said to be lighter.

Oh, and IceWM is a standalone window manager. Using just a WM is about as light as it gets, although you forsake nice things like panels without running separate programs.

---

### Post by win4thebin on 2008-11-19
*Sudo apt-get install kubuntu-desktop* if you want kde.

---

### Post by Tony Williams on 2008-11-20
> **snova said:**
> Ok, interesting subject...

X is a server that controls the display. All graphics ultimately go through X.

The Display Manager is the program that is run first (or something like that). It asks you for your password and permits you a login.

A Window Manager is responsible for the borders around windows, as well as the titlebar. Without a running WM, it's about impossible to do anything, not even so much as to resize/move a window. Try killing Metacity (or Kwin for KDE) if you want to see what life is like without one (it's awful).

A Desktop Environment is really just a collection of programs. Several of them running together work to procure you a useable GUI. For Gnome, for example, there is a program controlling the panels, a program controlling the background, and so on, whereas KDE has similar (in functionality, that is) but different programs. Gnome and KDE both include their own window manager.

They interact quite well, there is no reason why you can't run one DE with your favorite applications from another.

A session... not completely sure. It seems to have two meanings. When logging in, it applies to which desktop environment you wish to start (there's a menu). When logged in, I think it's essentially a set of running programs along with their state, so that you can logout and log back in again and have everything the way it was before.

If you want to try KDE, just install the "kde" package. The "kubuntu-desktop" package depends on KDE but also a few other things, one of which is branding...

There is also XFCE, which is said to be lighter.

Oh, and IceWM is a standalone window manager. Using just a WM is about as light as it gets, although you forsake nice things like panels without running separate programs.

Great post.

---

