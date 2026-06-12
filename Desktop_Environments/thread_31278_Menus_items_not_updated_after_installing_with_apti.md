---
title: "Menus items not updated after installing with aptitude"
date: 2005-05-02
forum: Desktop Environments
---

### Post by mightydavefish on 2005-05-02
So I'm trying out Ubuntu and Kubuntu, but I'm having a similar problem in each.  When I install apps using aptitude nothing shows up on the menu.  I am far from a newbie and am used to dealing with weird issues, but this is frustrating.  I have to manually create entries for everything and that doesn't work the same as the entries they create for themselves on every other distro I've every tried.  I really find this baffling since it is a show stopper for new folks and I'm amazed it would be a problem in an official release.   How is it that no one else mentions this on the forums?  I've tried both Ubuntu and Kubuntu on three different machines and they all exhibit this behavior.
Is there something simple I'm missing, or is this a known problem?  
Is there something I have to run after installing apps that isn't running automatically?  This is problem that prevents me from using Ubuntu on any machine but my own where I can manually fix the missing menu entries.

---

### Post by Gandalf on 2005-05-02
[QUOTE=mightydavefish]So I'm trying out Ubuntu and Kubuntu, but I'm having a similar problem in each.  When I install apps using aptitude nothing shows up on the menu.  I am far from a newbie and am used to dealing with weird issues, but this is frustrating.  I have to manually create entries for everything and that doesn't work the same as the entries they create for themselves on every other distro I've every tried.  I really find this baffling since it is a show stopper for new folks and I'm amazed it would be a problem in an official release.   How is it that no one else mentions this on the forums?  I've tried both Ubuntu and Kubuntu on three different machines and they all exhibit this behavior.
Is there something simple I'm missing, or is this a known problem?  
Is there something I have to run after installing apps that isn't running automatically?  This is problem that prevents me from using Ubuntu on any machine but my own where I can manually fix the missing menu entries.[/QUOTE]
 give an example, which package for example don't show a menu when you apt-get it

---

### Post by Stormy Eyes on 2005-05-02
1. Open terminal
2. Type "killall gnome-panel".
3. Press "Enter".
4. Problem solved.

---

### Post by andremarcel on 2005-05-04
I have the same problem. Restarting the panel has no effect.
Has anybody an idea?

---

