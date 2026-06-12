---
title: "Is there a way to run an XFCE4 applet on gnome panel?"
date: 2007-01-06
forum: Desktop Environments
---

### Post by jbus on 2007-01-06
I know I can run gnome applets on the xfce4 panel, but I want to do it the other way around. Why??? Because I use gnome, but I currently don't use the gnome panel at the bottom of my screen because I can't stand the window list applet that wastes so much space and is a real eyesore in my opinion. That, and the window selector applet seems completely useless to me. 

Instead I have installed the xfce4 panel because it has one applet that the gnome panel really needs. The iconbox applet, which shows only the icons for the running tasks and gives a window title only if you hover over it.  I have attached a screenshot the xfce panel running on my system. You can see that the iconbox applet is on the far right and I only have Swiftfox running. This works for now, but I would prefer to use the gnome panel because it is easier to configure and add launchers with (drag and drop) to than the xfce panel is. 

So, does anyone know if it is possible to use the xfce iconbox applet on the gnome panel or if there is some hacked version of the window list applet that will behave like the icon box??? I really don't understand why such an applet doesn't yet exist got gnome. It seem that this would be fairly simple to accomplish, though that's coming from a non-developer. Anyway, much appreciation to anyone that can help me.

---

### Post by MetalMusicAddict on 2007-01-06
I think the Window Selector does something similar. Otherwise I see nothing there you cant do in Gnome panels.

---

### Post by jbus on 2007-01-06
> **MetalMusicAddict said:**
> I think the Window Selector does something similar. Otherwise I see nothing there you cant do in Gnome panels.

The window selector applet only shows a tiny icon of the currently active application. You have to click on it to get a list of all the running aplications. The xfce iconbox applet instead shows the icons of ALL the running applications on the panel.

I'm attaching another screenshot with two more applications running. All of the icons to the right of the Trash indicate running applications. This is the functionality I would like on the gnome panel.

---

### Post by orb9220 on 2007-01-07
Well the window list applet shows running apps, and if you change the max width to like 100 on the size tab then it will just show the icon of app running.

Also be sure to select  Show windows from all workspaces then all running apps will be present no mater of desktop.

Hope this helps

---

### Post by jbus on 2007-01-07
> **orb9220 said:**
> Well the window list applet shows running apps, and if you change the max width to like 100 on the size tab then it will just show the icon of app running.

Also be sure to select  Show windows from all workspaces then all running apps will be present no mater of desktop.

Hope this helps


Thanks, I have tried this before with very poor results. With the window list applet the size of the buttons vary greatly depending on how many applications are running regardless of what you set the max. and min. width to, and there is no way to make the icons scale to the size of the panel either.

---

### Post by tweedledee on 2007-01-09
> **jbus said:**
> So, does anyone know if it is possible to use the xfce iconbox applet on the gnome panel or if there is some hacked version of the window list applet that will behave like the icon box??? I really don't understand why such an applet doesn't yet exist got gnome. It seem that this would be fairly simple to accomplish, though that's coming from a non-developer. Anyway, much appreciation to anyone that can help me.

I don't think so.  I've found the XFCE panels to be much more flexible than the gnome panels, and personally just run one of each, with the XFCE panel managing my windows and the gnome panel holding the menu and launchers (because you are correct that those are easier to configure with the gnome panel).

---

### Post by jbus on 2007-01-10
Thanks for the reply tweedledee,

I'm glad to see I'm not the only one that dislikes the window list applet. What really puzzles me is why an applet similar to XFCE's iconbox doesn't exist for the gnome panel. 

Actually, the lack of a large number of gnome panel applets surprises me as well. Hasn't the applet capability been around long enough in gnome that we should all be swimming in community created gnome applets? Shouldn't there be a gnome applet website loaded with different kinds of applets to download and easily install? What's up with this??? Is this due to lack of imagination on the part of gnome users or is there some kind of restrictions that gnome devs have on these applets that prevent people from making more of them?

---

### Post by urukrama on 2007-01-10
> **jbus said:**
> I know I can run gnome applets on the xfce4 panel

How do you do that? Sorry to move slightly off topic.

---

### Post by jbus on 2007-01-10
> **urukrama said:**
> How do you do that? Sorry to move slightly off topic.

Install xfce4-xfapplet-plugin and all your gnome applets will be available to use in your xfce4 panels.

---

### Post by tweedledee on 2007-01-13
> **jbus said:**
> Thanks for the reply tweedledee,

I'm glad to see I'm not the only one that dislikes the window list applet. What really puzzles me is why an applet similar to XFCE's iconbox doesn't exist for the gnome panel. 

Actually, the lack of a large number of gnome panel applets surprises me as well. Hasn't the applet capability been around long enough in gnome that we should all be swimming in community created gnome applets? Shouldn't there be a gnome applet website loaded with different kinds of applets to download and easily install? What's up with this??? Is this due to lack of imagination on the part of gnome users or is there some kind of restrictions that gnome devs have on these applets that prevent people from making more of them?

You can find a number of threads on here (and elsewhere) complaining about the Gnome developers.  The basic issue is that they code Gnome so it only provides so much flexibility; the rest is all hard-coded (e.g., that's why you can't configure the "Places" menu).  I think Gnome is overall better than XFCE or KDE right now, but I hope that with a little more development XFCE offers much of the same "ease of use" functionality available in Gnome will still allowing you to extend it in many different directions (as you can, as the panel plugin applet shows).

I'm not much of a Gnome historian, but there is also a tendency of the Gnome developers to limit the number of applets available.  There have been applets removed in the past without a new applet offering all of the same functions.

---

