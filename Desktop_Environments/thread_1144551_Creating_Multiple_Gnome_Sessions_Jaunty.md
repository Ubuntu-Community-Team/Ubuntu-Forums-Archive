---
title: "Creating Multiple Gnome Sessions Jaunty"
date: 2009-04-30
forum: Desktop Environments
---

### Post by exsilium on 2009-04-30
I've been trying to create multiple gnome sessions per user in jaunty but had no luck everything i've found says to use the 'Sessions Option' tab in gnome-session-properties but i see no such tab. the idea is to have several differant sessions one for work, one for home, etc. Each with its own complete set of setting keybindings, backgrounds, etc.

---

### Post by x1a4 on 2009-04-30
Hi,
[This HOWTO]("http://hex1a4.net/xubuntu/howto/03/") shows how to customize VTs including how to have multiple instances of GDM/X on start-up.  

You can also just run **gdmflexiserver**.

---

### Post by exsilium on 2009-05-01
Thanks for the reply but both your suggestions seem to deal with running multiple sessions at the same time.

what i'm trying to is at gdm under options you can select what session you want

last logged in
gnome
failsafe gnome
etc.

what i'd like to do is add more gnome entries such as one for work and one for home with differant settings so far i've been able to add anothe gnome entry but they both use the exact same settings.

i think the trick is to use the --default-session-key=KEY option for gnome-session which is used to start the session but right now i'm having no luck understanding what the KEY value can be or reparsents

---

### Post by Lantesh on 2009-06-02
I'm looking to do the same thing as exsilium.  Does anyone have any information on this?

---

