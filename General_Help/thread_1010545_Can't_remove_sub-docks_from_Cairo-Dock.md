---
title: "Can't remove sub-docks from Cairo-Dock"
date: 2008-12-13
forum: General Help
---

### Post by Izek on 2008-12-13
As the thread title says, I can't remove them, or don't know how to. I would like to remove a sub-dock. I can't right-click it because all it gives me is the cairo-dock menu option.

Also, none of the "Preferences" buttons do anything in the configuration of cairo-dock.

---

### Post by gettinoriginal on 2008-12-13
Can you just go into the ~/.cairo-dock/current_theme/launchers folder, and search for a .desktop file that controls that dock ??  I don't have facts as I don't use cairo-dock.  Just making a guess here.

---

### Post by Izek on 2008-12-13
There are no hidden files in the current_theme folder, meaning no files that start with a period.

---

### Post by gettinoriginal on 2008-12-13
ok, the config files should be in ~ / .config / cairo-dock, can you edit them in terminal ??

---

### Post by Izek on 2008-12-13
I think I'm going to leave cairo-dock alone, I like AWN much better anyway.

---

### Post by gettinoriginal on 2008-12-13
+1 for that statement  LOL

---

### Post by dilodicus on 2010-11-21
I know this is an old post, but it shows up high in google when you search for a solution to this problem, so I shall give you the solution to this problem in the hope others will find this.

In Cairo Dock there doesn't seem to be a way to just remove a dock, but if you remove all launchers individually or move them to another dock, one by one, then once the last one is gone, the dock ceases to exist! :)

why the developers didn't just put an a command to remove the dock in one go, I do not know, but this method seems to work fine :)

---

### Post by Yarbo on 2011-02-10
> **dilodicus said:**
> I know this is an old post, but it shows up high in google when you search for a solution to this problem, so I shall give you the solution to this problem in the hope others will find this.

In Cairo Dock there doesn't seem to be a way to just remove a dock, but if you remove all launchers individually or move them to another dock, one by one, then once the last one is gone, the dock ceases to exist! :)

why the developers didn't just put an a command to remove the dock in one go, I do not know, but this method seems to work fine :)

Hmm, I'm experiencing some different behavior with Cairo-Dock. I'm using 10.10, if that makes any difference.  

I chose to use to Humanity-Dock theme, cause I felt it fit nicely with Ubuntu's overall appearance. However, I didn't like the two docks that appeared at the top corners of the screen, so I moved all of the items off of them.  The dock at the top right of the screen vanished as expected, however the dock at the top left of the screen remains, as indicated in the attached screenshot.

As you can see, a small square appears, and it prevents me from accessing buttons or menus in that region of the screen.  I've made it less annoying by moving it to the bottom left of the screen (I set the main dock area to be reserved, so not much is going on in that corner.)

I've tried looking in ~/.config/cairo-dock/ to see if there was anything I could do there ( delete or modify any files or conf files, but I was unable to find anything).

I can move icons to the dock as well, and then if I move them off again, it still doesn't disappear.   If anyone knows a solution to this problem, I'd appreciate it.

---

### Post by wilcsnyder on 2011-02-20
You can try to go to ~/.config/cairo-dock/current_theme/launchers. There are listed all the launchers and docks. Maybe look for the container files. For example, 02container.desktop. Then open these one by one using a text editor, and find the one you don't want. Then just delete that particular container.desktop file. Don't know if this will help your particular problem or not.

---

