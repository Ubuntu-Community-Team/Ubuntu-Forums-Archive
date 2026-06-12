---
title: "How to put dockbarx gnome applet on unity panel?"
date: 2011-05-15
forum: Desktop Environments
---

### Post by vickoxy on 2011-05-15
Hi,
i am using Unity on my Ubuntu 11.04 64bit. I like some gnome applets. So, e.g. gnome-gmail-notifier is working perfectly with unity panel. Does anyone knows how to put dockbarX applet to unity panel?

---

### Post by vickoxy on 2011-05-16
No one?

---

### Post by wildmanne39 on 2011-05-16
> **vickoxy said:**
> Hi,
i am using Unity on my Ubuntu 11.04 64bit. I like some gnome applets. So, e.g. gnome-gmail-notifier is working perfectly with unity panel. Does anyone knows how to put dockbarX applet to unity panel?
If it will let you all you need to do is start the program then go to launcher right click on the icon that you want there and click keep in launcher.):P

---

### Post by Copper Bezel on 2011-05-17
The Unity panel doesn't quite work like that. It's rather attached to its Docky parts and doesn't support an alternative task switcher.

Personally, I use a _[fairly Unity-like]("http://ubuntuforums.org/showthread.php?t=1714111")_ configuration of Avant Window Navigator to keep DockBarX while using the Unity workflow, with Synapse as a Dash alternative.

---

### Post by vickoxy on 2011-05-17
Well, i just want to avoid to have three sides filled with panels/launchers. Thought that there would be solution to put dockbary to unity panel as it works with gnome-gmail-notifier...

---

### Post by Copper Bezel on 2011-05-17
gnome-gmail-notifier is actually just a notification area icon. (It works under AWN, too.) = ) 

But yes, DockBarX running in a third panel of one kind or another would be absurd. You can auto-hide the Unity Launcher and disable all the things that can make it reappear from CompizConfig, then replace it with something containing DockBar, but there are no *applets* you can add to the Unity interface. Systray indicators are a different thing.

Edited with slightly more useful information. = )

---

### Post by vickoxy on 2011-05-17
Well, as said i don´t want to install another dock. So, it is not possible to make it work in unity panel?

---

### Post by Copper Bezel on 2011-05-17
Sorry about that; I was in the process of editng my post with some slightly more useful information. I wasn't suggesting a third panel. If you want DockBarX, you'll need to replace either the Unity Launcher or the whole Unity plugin with something else.

---

### Post by vickoxy on 2011-05-17
Thanks. Well i am switching between unity and gnome in last few days. When i use Ubuntu, i have many windows opened (pdf books, web browser, few libreoffice documents) and i am used to have all this windows just in one notification area only one click away. Using unity starter here was not so practical solution for me...

---

### Post by Copper Bezel on 2011-05-17
Yeah, I could see that. Sticking with the Gnome Panel in the Classic desktop probably makes the most sense if you're dealing with a lot of documents that you need to distinguish by label rather than applications you can distinguish by icon. 

To avoid future confusion with terminology, since I think a few of these are getting switched around a bit:

The bar at the top in Unity is still called a *Panel*.

The bar at the left is referred to as the *Launcher*. The capital is important, as *launcher* can still refer to a desktop icon.

The *notification area* or *systray* is just the little row of icons and menus at the right end of the Unity Panel (and the Gnome Panel when it's using default settings.) The term *indicator applet area* is sometimes used as well. In Gnome Panel or AWN, the notification area and indicator applet area are treated as separate things and together make up the system tray.

Unity, unlike almost any other dock or panel, really offers no customization options other than changing the Launcher items or adding applications that display applets in the systray. DockBarX was originally written for the Gnome Panel and runs in AWN and the XFCE panel as well, but the Unity Panel is a completely separate code base from the Gnome Panel, written by different developers (even though they look identical by default.)

---

### Post by vickoxy on 2011-05-17
Thanks a lot for explanation! :popcorn: 
Well, i will just have to use for a while both desktops...

---

