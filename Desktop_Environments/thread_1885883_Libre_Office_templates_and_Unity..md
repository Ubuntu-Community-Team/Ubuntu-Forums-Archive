---
title: "Libre Office templates and Unity."
date: 2011-11-24
forum: Desktop Environments
---

### Post by ferulebezel on 2011-11-24
Under Gnome I was able to place frequently used templates on the panel to quickly start a file based on them.  How do I do this with Unity?

---

### Post by typhoon_tip on 2011-11-24
> **ferulebezel said:**
> Under Gnome I was able to place frequently used templates on the panel to quickly start a file based on them.  How do I do this with Unity?

You can alternatively copy them into the $HOME$/Templates folder, and then when you right click with Nautilus and "Create New Document" over any folder, it will show your templates there and create one.

---

### Post by ferulebezel on 2011-11-24
That doesn't really solve the problem.

The whole point was to have them easily accessible, not covered by maximized windows nor under several layers of menus.  

Thanks anyway.

---

### Post by typhoon_tip on 2011-11-24
> **ferulebezel said:**
> That doesn't really solve the problem.

The whole point was to have them easily accessible, not covered by maximized windows nor under several layers of menus.  

Thanks anyway.

It can be done. You just need to create .Desktop files to be placed where Unity pick up the launchers for its bar. I am sure I have read it in exactly this room of the forum.

---

### Post by Copper Bezel on 2011-11-27
Yes, anything that you can create as a launcher for the old Gnome Panel, you can make as a menu entry in alacarte ("Main Menu"). Then it's in Unity's Dash and can be pinned to the Unity Launcher.

---

### Post by ferulebezel on 2011-11-28
I tried alacarte and it didn't work.  The only thing I could do was to create a new menu (which I assume is actually a directory somewhere).  Even then it was never displayed, even after logging out.  I tried this in Unity,Gnome and Gnome classic.  It wouldn't even let me create a launcher item.  

From reading some other threads it looks like I can only do this globally.  That sucks.  I like to maintain multiple user accounts for different tasks (It keeps me from getting distracted.).  

How can I modify the menus for just a single user account?

I was easy in Gnome 2.

---

### Post by Copper Bezel on 2011-11-28
What you're creating is a .desktop file in ~/.local/share/applications. After selecting one of the categories in Alacarte, you should be able to click the New Item button, then set the name, command, and icon for that item. Otherwise, you could create the .desktop file manually; as long as it's in that folder, it'll show in the Unity Dash. You can use one of the existing .desktop files in /usr/share/applications as a template if it comes to that (and open it in gedit.)

None of this has to be done globally - in fact, it would be an extra step to do so. You'd need to create the .desktop file and then move it to /usr/share/applications - so you'd be doing it for your own user account first, anyway.

---

### Post by 3rdalbum on 2011-11-28
> **ferulebezel said:**
> I tried alacarte and it didn't work.  The only thing I could do was to create a new menu (which I assume is actually a directory somewhere).  Even then it was never displayed, even after logging out.  I tried this in Unity,Gnome and Gnome classic.  It wouldn't even let me create a launcher item.

You need to create a menu ITEM, not a menu. Create it in one of the existing "menus" in Alacarte (for example, in Accessories). Open the Dash, click the Applications lense and filter the results by "Accessories" and your new launcher will be in there. Drag it to the Launcher and you're done.

You could also try modifying the Libreoffice launcher icon's quicklist, but that's currently a bit more fiddly because there's no easy quicklist editor program.

---

### Post by ferulebezel on 2011-11-29
I managed to do something useful.  It's ugly but it works.

Instead of doing a location I did an application with the template as a command line argument.  It works but I won't be able to explain it to the people at work who are used to Mac and Windows.  I'd like it for them to have the logs that they need to access right there in front of them, instead of making them use nautilus or having me perform this horrible solution on everybody's account.  

This was much easier in Gnome 2 where people could just drag the template or file to the top bar.

---

### Post by Copper Bezel on 2011-11-29
Well, you couldn't do it under Windows or Mac, either. When you use software for use cases it's not designed for, you have to be prepared for the fact that the jerry rig you've applied might not always work.

What you need is a Templates lens for the Unity Launcher, which I don't know anything about writing, or a Quicklist for Libreoffice, so that right-clicking its Launcher icon will give you a list of templates, but the quicklist, unlike the lens, would need each entry added manually, which defeats the purpose a little. For now, the sensible thing would be to simply pull up your templates from the Dash search.

---

