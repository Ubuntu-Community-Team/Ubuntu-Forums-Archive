---
title: "Script to add launcher on desktop (or panel)"
date: 2006-10-11
forum: Desktop Environments
---

### Post by bazzer on 2006-10-11
Hi all
I'm trying to add a launcher to the desktop (or the panel at the top) to mimic the one in 'System>Administration>Printing'.

I know I can just drag that sucker out from the menu and plonk it on the desktop or the panel, but I want to do this in a script. A startup script, no less.

I've found that you can edit the gconf.xml files but there are hundreds of them and the chances of me cocking up the entire install blindly flailing around for the correct one are quite high! :D
Anyone done this before?

---

### Post by s_p_a_r_k_y on 2006-10-11
um, add 
gnome-cups-manager
to System->Preferences->Sessions and go to Startup Programs

that will cause it to startup on login

---

### Post by bazzer on 2006-10-12
Yeah I know that,  but it's not doing it by a script....

---

### Post by CatKiller on 2006-10-12
Goodness knows why you want to do it as a script, rather than using the tools you already have at your disposal. Anyway, desktop launchers are .desktop files. I'd imagine that a reasonably sane way to do an insane thing would be to use the drag-and-drop method to get a sample .desktop file for what you want. Then copy/move that somewhere else where your users can read it. Then, on startup, copy that file to the user's Desktop.

---

### Post by bazzer on 2006-10-12
The reason I'm doing it as a script is that I'm trying to set up a PC with all new users having a 'default desktop' and that means all the icons need to be in the same place etc.

What are these other tools at my disposal then?

---

### Post by CatKiller on 2006-10-12
> **bazzer said:**
> What are these other tools at my disposal then?

Well, you'd already dismissed the drag-to-desktop in your original post, and the Session Manager, in favour of some script that you haven't written yet.

> The reason I'm doing it as a script is that I'm trying to set up a PC with all new users having a 'default desktop' and that means all the icons need to be in the same place etc.

It's easy enough to put launchers on the Desktops of new users. That sample .desktop file that you've made can be put in /etc/skel/Desktop - create the Desktop if it isn't there already - and then it will be included on the Desktop of all new users.

EDIT: The panel isn't quite so straightforward. Panel geometry and applications are handled by gconf. You'll need to establish the settings for getting the launcher (still a .desktop file) where you want it on the panel by putting it there on one account and then inspecting the settings for the geometry in gconf-editor. Once you've got all the information that you need, default gconf settings for new users can be fiddled with using **update-gconf-defaults**.

---

### Post by bazzer on 2006-10-12
> **CatKiller said:**
> 
It's easy enough to put launchers on the Desktops of new users. That sample .desktop file that you've made can be put in /etc/skel/Desktop - create the Desktop if it isn't there already - and then it will be included on the Desktop of all new users.
Ah I see, that's what I was after as far as the desktop is concerned....
> **CatKiller said:**
> 
EDIT: The panel isn't quite so straightforward. Panel geometry and applications are handled by gconf. You'll need to establish the settings for getting the launcher (still a .desktop file) where you want it on the panel by putting it there on one account and then inspecting the settings for the geometry in gconf-editor. Once you've got all the information that you need, default gconf settings for new users can be fiddled with using **update-gconf-defaults**.
And this is precisely what I was asking in the first place! As i said, there are loads of gconf.xml files to choose from, how would I know which one. I know I can go into gconf-editor and click and change stuff, but as you can see, that's not the desired result.

---

### Post by CatKiller on 2006-10-12
> **bazzer said:**
> And this is precisely what I was asking in the first place! As i said, there are loads of gconf.xml files to choose from, how would I know which one. I know I can go into gconf-editor and click and change stuff, but as you can see, that's not the desired result.

No, the idea is not to click and change stuff. The idea is to poke around for the values that you want. gconf-editor is much more sensible for this than trying to squeeze insight out of the raw XML.

For example, under apps/panel i have a key called applet_1 that tells me all I could wish to know about getting a Lunar clock locked 137 pixels in on the bottom panel of the right screen of my dual-monitor setup.

And what you actually asked for in the first place, as far as I can tell, was how to write a startup script to create icons on the desktop to fiddle with the print settings.

---

### Post by bazzer on 2006-10-12
> **CatKiller said:**
> 
And what you actually asked for in the first place, as far as I can tell, was how to write a startup script to create icons on the desktop to fiddle with the print settings.

So where's the answer then>?!?>?!!

---

### Post by bazzer on 2006-10-12
Nope, I'm sorry I can't let this one go...
> **CatKiller said:**
> No, the idea is not to click and change stuff. The idea is to poke around for the values that you want. gconf-editor is much more sensible for this than trying to squeeze insight out of the raw XML.
Ok, fair point, it's exactly what I'm looking through now to see if I can locate any more information about the gnome-cups-manager launcher that I've plonked on the panel. Unfortunately, the gconf-editor isn't all that intuitive, hence my original question "Anyone done this before?".

> **CatKiller said:**
> For example, under apps/panel i have a key called applet_1 that tells me all I could wish to know about getting a Lunar clock locked 137 pixels in on the bottom panel of the right screen of my dual-monitor setup.
And so, does this information you speak of allow you to create an object by means of copying a file or by a script? I have an object called 'object_0' which relates to the launcher in question, but there's not even any references to the name of the icon, much less what it launches in that key. I need to find all references to this 'object_0' and copy the settings down. Hence my original question "Anyone done this before?".

> **CatKiller said:**
> And what you actually asked for in the first place, as far as I can tell, was how to write a startup script to create icons on the desktop to fiddle with the print settings.
...see where I'm going with this now?:)

---

### Post by CatKiller on 2006-10-12
> **bazzer said:**
> So where's the answer then>?!?>?!!

You'll get no such answer from me. I don't even know if it's possible to do so as a script per se, much less how to do it. Instead, I told you about how new user settings are defined and the tools that do it, which you seemed interested in for a while. If you still want to do it as a script you'll have to hope someone insane enough to want to script the creation of files, rather than simply copying them to an appropriate place, comes along.

---

### Post by bazzer on 2006-10-12
Ok, anyone else got something more constructive?
I'll explain again for anyone who's listening...
I want to be able to put the gnome-cups-manager in this position on the panel for all users. I need to be able to do this in a script, as I'm building a 'kiosk' type machine that will be duplicated many, many times - so 'drag and drop and click here and there' won't be suitable.
[IMG]http://www.barryrlee.f2s.com/stuff/cups-manager.png[/IMG]
Thanks!:)

---

