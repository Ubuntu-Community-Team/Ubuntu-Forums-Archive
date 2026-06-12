---
title: "firefox problems"
date: 2009-06-21
forum: General Help
---

### Post by xGutsAndGloryx on 2009-06-21
how do i completely uninstall and reinstall firefox? i tried going through add and remove programs. can someone please assist me?

---

### Post by starcraft.man on 2009-06-21
Why do you need to reinstall firefox? If you describe the nature of the problem we can better help. More details is always better.

---

### Post by xGutsAndGloryx on 2009-06-21
the minimize, maximize and close button have disappeared from the top right hand corner.

---

### Post by 3rdalbum on 2009-06-21
Reinstalling Firefox won't actually do a lot unless you're sure that the program itself is corrupted. As the Firefox executable is owned by root and run as a regular user, it will not change.

If you want to start afresh with Firefox, you should move or rename the ".mozilla" directory inside your home directory. This contains the user settings. When you next start Firefox, it won't be able to find the user settings and will create new, blank settings just like it would have done when you first installed Firefox (or when you first installed Ubuntu).

If this doesn't solve your problem and you think it might be a corrupted Firefox itself, you can mark all Firefox packages for reinstallation in Synaptic Package Manager.

---

### Post by T.J. on 2009-06-21
Has the title of the window, and borders disappeared too?  If so, you might be using Compiz, which technically is an unstable window manager.   It usually works well, but it may have an issue with your video driver. Under Gnome, Ubuntu uses a script to load the window manager, instead of loading it directly.  Sometimes this causes glitches as well.



Try opening a terminal window and typing in:

metacity --replace &


I'm sorry to say that not all Linux video drivers are good ones, because the companies that make the cards refuse to release certain information.

T.J.

---

### Post by xGutsAndGloryx on 2009-06-21
> **3rdalbum said:**
> Reinstalling Firefox won't actually do a lot unless you're sure that the program itself is corrupted. As the Firefox executable is owned by root and run as a regular user, it will not change.

If you want to start afresh with Firefox, you should move or rename the ".mozilla" directory inside your home directory. This contains the user settings. When you next start Firefox, it won't be able to find the user settings and will create new, blank settings just like it would have done when you first installed Firefox (or when you first installed Ubuntu).

If this doesn't solve your problem and you think it might be a corrupted Firefox itself, you can mark all Firefox packages for reinstallation in Synaptic Package Manager.


ok! i am still learning how to navigate through the file system and home directory. how do i get to where mozilla is stored?

---

### Post by xGutsAndGloryx on 2009-06-21
everything else in firefox works perfect. its just the minimize, maximize, and close buttons in the top right hand corner that have disappeared.

---

### Post by xGutsAndGloryx on 2009-06-21
.

---

### Post by Johnny B on 2009-06-21
> **xGutsAndGloryx said:**
> everything else in firefox works perfect. its just the minimize, maximize, and close buttons in the top right hand corner that have disappeared.

this is usually a problem with compiz, try disabling it

---

### Post by JordyD on 2009-06-21
> **xGutsAndGloryx said:**
> ok! i am still learning how to navigate through the file system and home directory. how do i get to where mozilla is stored?

Open your home directory, type "Ctrl-H", then start typing ".mozilla", this will start searching. If it's not searching, it may be because the focus is on the wrong part of the app, so click in the right-hand portionof it, holding all the folders, and try again. When you find it, you can back it up by just moving it to .mozilla.bak or something.

> this is usually a problem with compiz, try disabling it

I would try this first. If you don't know how to disable it, you can go to **System > Preferences > Appearance**, there you can find the Visual Effects settings, set it to "None".

---

### Post by xGutsAndGloryx on 2009-06-21
thanks

---

### Post by JordyD on 2009-06-21
> **xGutsAndGloryx said:**
> thanks

Does this mean your problem was fixed?

---

