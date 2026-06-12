---
title: "sidebar thing very erratic"
date: 2011-05-03
forum: Desktop Environments
---

### Post by stdragon on 2011-05-03
I'm not sure what to call the semi-transparent sidebar with a random collection of unconfigurable icons, but I don't think it's working properly.

1. When I move my mouse to the left edge of the screen, it doesn't always appear. Sometimes I have to move my mouse back and forth, back and forth, several times.

2. What it's doing right now is even worse... it appears, but as soon as I move the mouse a *little* bit to the right to actually click an icon, it disappears.

What is causing this? Surely it's a bug? How do I make the sidebar the absolute top priority for the screen edge so that it always catches it and appears?

Also, how do I configure it? I can't right-click on the sidebar itself. I can right-click and remove some icons. Other icons, like the grayed-out (but still active) "recent files" thing cannot be removed.

---

### Post by Copper Bezel on 2011-05-04
The behavior you're describing does sound like a bug. The Launcher shouldn't disappear while your cursor is hovering it. Check its settings in CompizConfig, but you might end up needing to file a bug. 

To get rid of the Recent Files lens, check out this guide to common Unity tweaks and fixes from [WebUpD8]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html") and scroll down a few screens. The gray color, by the way, isn't meant to signify inactive items in the Launcher - I think it distinguishes lenses and applets from applications.

I'm assuming you're using Compiz Unity - if you're using Unity 2D, it's a whole different beast.

---

### Post by srinig on 2011-05-04
The launcher does play this hide and seek game when I hover over the launcher icon in the top left of the screen. When I hover over that icon, the launcher partly appears, and when I try to click an application, it disappears. But it appears fully and behaves well and I take the mouse pointer to the absolute left or top-left of the screen. In your case, as you say it happens even when you go to the left edge of the screen, it could be a bug. Or maybe, your monitor and screen settings need a tweak, I don't know.

Or you can just keep the launcher visible all the time. Try this: press Alt + F2 and type 'gconf-editor'. Go to apps -> compiz-1 -> plugins -> unityshell -> screen0 -> options. Set the 'launcher_hide_mode' to 0.

---

