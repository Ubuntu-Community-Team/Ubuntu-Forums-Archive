---
title: "Gnome3 on Natty questions"
date: 2011-07-11
forum: Desktop Environments
---

### Post by austerus on 2011-07-11
Hello everyone,

I have recently installed Natty Narwhal and all seems fine and dandy but I already miss Gnome. Since Gnome 3 exists and I would like to try it, I want to ask: does anyone have a safe way of installing Gnome 3 with the gnome shell? I know that with Unity I can choose Ubuntu Classic login to use Gnome 2 with the Unity theme but that's not what I'm looking for.

I saw several tentative discussions about Gnome3 but no definitive conclusion regarding Gnome 3 on Natty.

I have tried to install Gnome 3 myself, by adding the ppa repository, doing a full update and then install gnome3 but the result was this:

after restarting, I got a Gnome option for login, but if I chose it then the login password box became a simple input box (no graphical elements as if all were stripped away) and even after a correct login the system would hang before I was sent back to login without any possibility to change the session type.

Could someone help? Thanks!

PS: with my default installation, the compiz config manager was missing from system settings and running 'ccsm' said that it wasn't installed. Trying to install compiz resulted in a message saying it is installed but trying to install ccsm result in a message saying it cannot be installed. Has this happened to anyone?

---

### Post by 3Miro on 2011-07-11
Unity is different interface (UI) for Gnome. In 11.04, Unity works as a different UI for Gnome 2. In 11.10, Ubuntu will come with Unity on top of Gnome 3.

Gnome 3 is not officially supported for Natty. You can only use an unofficial repository and some of those are rather buggy. However, some people have gotten them work.

Gnome-shell cannot run together with compiz. That's why Gnome 3 probably uninstalls compiz. Since Unity is a plugin for compiz, you cannot have Unity and Gnome 3 installed at the same time (you will have that in 11.10).

---

### Post by bladz01 on 2011-07-11
This makes me miss 10.10.  I strongly dislike Unity and mis my desktop effects.  Maybe I am too much of a noobcake to get it up and running correctly.

---

### Post by 3Miro on 2011-07-11
> **bladz01 said:**
> This makes me miss 10.10.  I strongly dislike Unity and mis my desktop effects.  Maybe I am too much of a noobcake to get it up and running correctly.

Unity is a plugin for compiz, so you can get most of the effects of 10.10. Only the cube is a bit tricky.

11.10 does come with Unit 2D/3D and optional Gnome-shell and Gnome-classic.

---

### Post by bladz01 on 2011-07-12
Well while waiting for 11.10 to come out is there a walk through for making CCSM work under Unity?  I don't really get how Unity is a plug in for Compiz?  I thought it was its own desktop environment like Gnome or KDE.

- Linux Nub

---

