---
title: "Is it Just ME?"
date: 2005-05-13
forum: Desktop Environments
---

### Post by fluideye on 2005-05-13
On the login screen there are several choices for sessions.  I have in mine:

>Last system session (or something to that effect)

>Default System Session

>Gnome

>KDE

>Gnome Failsafe

>Failsafe Terminal

So if I choose KDE I am taken to what looks like would be Kubuntu.  I haven't installed any KDE packages that I am aware of and haven't seen any discussions concerning this here in the forums, ubuntuguide.org, or google.  Does KDE Desktop Environment 3.4 come with Ubuntu?  I am confused and don't know enough about gnome and KDE differences to determine what I'm seeing.  Is it safe to set KDE as my default system session and if so, how does it work meaning would I use g & k apps?  

Help???

---

### Post by bored2k on 2005-05-13
Maybe you installed an applications that needs KDE libs like K3B or something, or perhaps kubuntu-desktop. To make sure KDE is working correctly, install kubuntu-desktop package. And no, you either geT GNOME or Kubuntu/KDE.

---

### Post by az on 2005-05-13
It did not get there by default.  You must have either installed it, or installed a package that depends on kde.

Check to see whether you have kubuntu-desktop installed.  If you do not and really like kde, you should install it so as to get the complete kubuntu experience.

You can run both gnome apps in kde and kde apps in gnome without a problem.

---

### Post by fluideye on 2005-05-13
I have kdesktop installed.  So this means that I can work in both environments without problems?  I've used kde with Mandrake 10.1 until I switched to Ubuntu and am not sure whether or not I want to stay in gnome so I'd like to test both for awhile and see which one I like.

---

### Post by az on 2005-05-13
kdesktop or kubuntu-desktop?

---

### Post by fluideye on 2005-05-13
kdestop

don't see kubuntu-desktop installed in the synaptic package manager.

---

### Post by fluideye on 2005-05-13
I see that I can install kubuntu-desktop thru synaptic package manager but havent done so and that's why I've posted this thread because I'm kinda scratching my head here wondering how I can log into a kde desktop

---

### Post by ssam on 2005-05-13
kubuntu-desktop is just a metapackage that installs kdedesktop and a load of kde applications.

---

### Post by az on 2005-05-13
Just like you can install an ubuntu base system, install gnome and not get things like synaptic or openoffice....

Actualy it is an example of how package management has many levels.  Ubuntu-desktop is the whole OS.  Gnome is the desktop environment.  Gnome libs are the libraries for gnome which use X.  X is connected to the shin-bone...


It is sometimes referred-to as "the stack" (not to be confused with kernel memory)

---

### Post by fluideye on 2005-05-14
that helps azz.  thanks to everyone for the feedback.

---

