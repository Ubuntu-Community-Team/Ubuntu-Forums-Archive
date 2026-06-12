---
title: "Gnome and KDE Concurrently"
date: 2007-08-15
forum: Desktop Environments
---

### Post by abrichr on 2007-08-15
I'd like to have Gnome running on one display, and KDE on the other, so that I can switch back and forth by pressing CTRL+ALT+F7 for Gnome and CTRL+ALT+F8 for KDE.

I've tried:

xinit -- :1 vt8
sudo kdm

But this just on the Kubuntu startup screen.  Any ideas?

---

### Post by K.Mandla on 2007-08-15
I've never heard of doing that, and to be honest, I don't know if it can be done. 

kdm is the login manager, though. That's why it's not starting KDE -- it's just the command for the login screen.

---

### Post by kellemes on 2007-08-16
Theoraticaly it can..
You will need to run 2 instances of Xorg and I'm sure there is a lot of crap you'll pump into..
I've heard of folks who tried, but I haven't heard of someone who succeeded.

---

### Post by Chaotic Thought on 2007-08-16
A simple way to get both running is to create two user accounts: For example, on my machine I might make two user accounts **chaotic-gnome** and **chaotic-kde**, and set each account's session accordingly. Just pretend that you have multiple people in your office, each who prefers a different desktop.

Of course, creating two user accounts and then sharing information between them introduces some other difficulties--once you have them both working separately, you'd need to setup a custom group in order to share both user's files. And if you wanted to make it so that program X would share settings between both accounts, you'd need to create symbolic links pointing to a separate shared settings directory. For example, **xmms** stores it's settings in $HOME/.xmms, so to arrange for both accounts to share XMMS settings, you might create links like this

**/home/chaotic-gnome/.xmms -> /home/chaotic-shared/.xmms**
**/home/chaotic-kde/.xmms -> /home/chaotic-shared/.xmms**

That way, it wouldn't matter whether you launched **xmms** under the chaotic-kde user or the chaotic-gnome user--both accounts would use the same settings. XMMS is only an example--pretty much all Linux programs store settings in a similarly-named "dot file" in your home directory. And besides, doing it this way might be good--there might be some settings that you _want_ to keep separately, and of course this can only be done (easily) with separate user accounts as I have described.

---

### Post by merlinus on 2007-08-16
[http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX)

I use it to run gnome, xfce and fluxbox without having to log out or close apps.

Thanks again, bodhi!

-merlin

---

### Post by K.Mandla on 2007-08-16
Cool. I learned something new today. ;)

---

