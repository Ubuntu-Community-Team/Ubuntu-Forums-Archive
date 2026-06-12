---
title: "Help teaching old dog new tricks please?"
date: 2009-11-13
forum: Desktop Environments
---

### Post by sandfly357 on 2009-11-13
OK, I admit it - I'm seriously confused by the Plasma thing. I simply cannot get my head around what is a "widget", an "applet" and all the various other objects that folks refer to here, and I'm having a real problem trying to get my desktop sorted. I really don't find any of this to be intuitive - it's probably just me, but that doesn't help! I need some simple, basic guidance to help me understand how it's all hung together, without assuming that I am already familiar with the differences between plasmoids, containers, widgets and protocol droids :smile:

Using Kubuntu Karmic, BTW.

As a simple example, how do I add an Icon (see, "oldspeak"!) to my desktop to launch a given executable? I know I can drag and drop from the Application menu, but what if the app, or script, I want to load isn't in the menu? Where are my desktop configuration files held (apart from all over the place by the looks of it!) When I do drag an Icon (or whatever it's supposed to be called) to my Desktop, what files/directories are modified? where's the link, or the copy of the "appl/widg/whatever/et" file stored?

Has anyone written an Introduction to Plasma for people who've only been used to Profiles and Desktops under Windows? And if so, where can I find it? 

Help!!!!

---

### Post by sakisds on 2009-11-13
Plasma have two things(as far as i know), widgets and panels.
Widgets are like windows sidebar things but they can be placed anywhere, even on bars(named panels).

Panels are like the bar you have the tray, the task manager and other things. You can create a lot of panels, on every side of the monitor and put anything on them. Also you can make them appear when you mouse over them or hide under windows and stuff.
(Anyway, the panel settings are a bit complex, so it may take some time to understand them.)

After some work i created the desktop from the screenshot attached. The bars in the bottom, right are panels and everything else are widgets.

(I didn't find any tutorials out there, so i had to find everything out by myself :P)

Edit: About the desktop folder, by default, there is a widget on the top left, that views anything in your /home/$username/Desktop(this can be changed). To view icons in the hole desktop, go to desktop settings(right click on the desktop) and set Desktop Activity Type to Folder view, and set which folder should be used by the desktop.

---

### Post by dazer26 on 2009-11-13
> **sandfly357 said:**
> OK, I admit it - I'm seriously confused by the Plasma thing. I simply cannot get my head around what is a "widget", an "applet" and all the various other objects that folks refer to here, and I'm having a real problem trying to get my desktop sorted. I really don't find any of this to be intuitive - it's probably just me, but that doesn't help! I need some simple, basic guidance to help me understand how it's all hung together, without assuming that I am already familiar with the differences between plasmoids, containers, widgets and protocol droids :smile:

Using Kubuntu Karmic, BTW.

As a simple example, how do I add an Icon (see, "oldspeak"!) to my desktop to launch a given executable? I know I can drag and drop from the Application menu, but what if the app, or script, I want to load isn't in the menu? Where are my desktop configuration files held (apart from all over the place by the looks of it!) When I do drag an Icon (or whatever it's supposed to be called) to my Desktop, what files/directories are modified? where's the link, or the copy of the "appl/widg/whatever/et" file stored?

Has anyone written an Introduction to Plasma for people who've only been used to Profiles and Desktops under Windows? And if so, where can I find it? 

Help!!!!

KDE has a million and one options and configurations, so if your new to it, I can see how it can be a bit confusing :)  My one issue with KDE right now is that unless you know where to look, it can take some searching to find what your looking for.  So the best advice I can give you is just to right click everything and see what comes up lol. 

If you have a program or script that is not in the menu you can add it easily.  Right click the K menu and go to "menu editor".  Here you can add menu entries, and it is as easy as showing it where the executable (or script) is in the file system.  

As the person above me said, you can change the desktop so it acts just like a windows desktop that you can put icons wherever you want.  I like the clean desktop look, so I use my /home folder as much as I can for all the random crap I download and install.  I have my desktop folder set to show the contents of my /home/user folder instead of the "desktop" folder so I can quickly get to my documents/downloads/video folders.

The KDE config files are stored in /home/user/.kde I believe, i'm not sure there is much you want to mess with in there tho.

"When I do drag an Icon (or whatever it's supposed to be called) to my Desktop, what files/directories are modified? where's the link, or the copy of the "appl/widg/whatever/et" file stored?"

I'm not too sure about all of this, why does it matter tho if you don't mind me asking?  I personally don't much care about how the underlying OS works, so long as when I put a link on my desktop it works :P.

---

### Post by sandfly357 on 2009-11-16
Thanks for the responses folks, much appreciated. I'll just keep plugging away and see how things develop, I guess. Right now I'm trying to work out where the "Desktop" container has disappeared to. I appear to have deleted it somehow....

I've always been one for knowing how the OS works, goes back to my Unix sysadmin days many years ago.

---

### Post by mrboojive on 2009-11-16
> **sandfly357 said:**
> Right now I'm trying to work out where the "Desktop" container has disappeared to.

If you didn't find it, that is the "Folder View" widget. Right click on the Desktop, go to "Add Widgets" and select "Folder View."

---

### Post by sandfly357 on 2009-11-18
You are a top man Mr Boojive!  Saved me much time, many thanks. After much experimentation, I think I might slowly be getting the hang of this after all :smile:

Thanks again folks...

---

### Post by Islington on 2009-11-18
A good way to think about it is that plasma is a canvas. Everything you drop onto into is a widget (also known informally as a plasmoid), this includes the panels, which are a basically a special container for widgets. 
The developers are trying to reduce the amount of jargon, so apologies for that. All the stuff you use on the gnome panel, such as the clock, the taskbar, the menu, all of these are widgets that can be dropped on the panel, or on to the general plasma canvas.

Now for a little bit of complication.

The space, that you know as your desktop, called an activity in plasma, has been traditionally treated as a special folder, where the file manager displays whatever is in that folder on this space. This can be done in plasma, but it is not all plasma can do. (to do this right click the desktop>>desktop settings>>desktop activity>>select folder view) This will cause your entire plasma canvas to act like the special folder, by causing the folder view widget to be in the background. You can also add more widgets on top of this activity.

You can also add activities to organize your widgets. This is still rather clunky in my opinion and involves zooming in and out (A.Seigo, mentioned that he would be coming up with something better than this.)

---

