---
title: "Some KDE and GDK Problems..."
date: 2011-04-20
forum: Desktop Environments
---

### Post by Neoxhadowespio on 2011-04-20
[SIZE=3]Well, hello! This is my first post in Ubuntu Forums (usually I just Google my problem). Anyway, I am using Ubuntu 10.10 Maverick Meerkat (Whats with the name?) with the default GDK which I happen to find very stable and love but also hate at the same time because it has barely any eye-candy at all. Anyway, I installed KDE (because its what all the pretty Linux desktops use) and gave it a go. My initial problem-black screen. But I had that taken care of. So I had a great time and all and then I restart and then FREEZE (which is VERY rare in something as great as Ubuntu, compared to Windows which I now hate). When it does that, mouse moves but thats it. I'm overall very smart and pretty good with operating system but Linux code is something I am yet to learn. Also, my Gnome desktop isn't really that bad although I'm desperate for one of those sidebars that show you the CPU and time and weather and crap. If you can solve either of my problems, please reply. By the way, I love Ubuntu ever since my Windows Vista crashed and I had it installed myself on the box.   [/SIZE]):P

---

### Post by Copper Bezel on 2011-04-20
You can actually make Gnome fairly glitzy, but if you'd prefer to work on solving the KDE problem, we'll need more details about the crash.

The sidebar you're referring to is called Conky. You can install it from the software center, but you'll need to download (or make) a configuration file for it, so do some Googling.

For full desktop glitz on Gnome, you'll want to look into the Emerald window decorator, settings for your Compiz window manager set via CompizConfig Settings Manager, and possibly a dock or alternate panel, if you're into that sort of thing, like Avant Window Navigator or Cairo Dock.

Those are some search terms to get you started. = )

---

### Post by Neoxhadowespio on 2011-04-21
[SIZE=3]Thanks! I have tried Emerald though I didn't like it too much; couldn't find the right themes. I also used to have a dock but I found that a bit restrictive. Also, what more can I tell you about the KDE crash?

[/SIZE]

---

### Post by Copper Bezel on 2011-04-21
Well, let's see - you said that on login in KDE, you could move the mouse pointer, but everything else froze? At what stage - was it the loading screen with the little icons, or did you get to the desktop? How long did you let it sit? Did any keyboard shortcuts work, like Alt+F2 for KRunner? (I'm not a KDE guy; I'm hoping that you'll say something that rings a bell for someone.)

For Emerald themes, the best ones tend to come with matching GTK+ themes. The [Divergence]("http://gnome-look.org/content/show.php/Divergence+IV+-+%22A+New+Hope%22?content=133892") series is popular lately; you might consider giving them another shot if you miss that KDE sparkle under Gnome.

Oh, one of my favorite little items to get a bit of depth to the desktop rather quickly is to turn on the "Blur Windows" and "Opacity, Brightness, and Saturation" plugins in ccsm, then use this string in each, for a new rule in Opacity set to 85% and for "Alpha Blur Windows":

```
(menu | popupmenu | dropdownmenu | tooltip)
```

---

### Post by Neoxhadowespio on 2011-04-21
Well whatever application I select; the little bouncy thingie starts doing its animation and then freezes, as does the rest of the computer except the mouse.

---

### Post by Neoxhadowespio on 2011-04-22
Thanks for the great theme! I love it. But where can I install the toolbar at the bottom? For Conky I wasn't able to install. Its quite complicated so is there any simpler alternative? And also, my Firefox theme-ish messed up a long time ago. It isn't too bad but it does look ugly and the (File|Edit|View|History|...etc) bar has black text on the black thing so it is difficult to read.

---

### Post by Neoxhadowespio on 2011-04-22
Actually, never mind the Firefox thing. I just found out about Personas!

---

### Post by Copper Bezel on 2011-04-22
Toolbar at the bottom? Do you mean the dock? It's Avant Window Navigator. You can install it from [_this_]("https://launchpad.net/~awn-testing/+archive/ppa") PPA. If you haven't installed from a PPA before, there are instructions on the page.

For an easier equivalent to Conky, you might look into Screenlets. There are system monitor and other widgets you can add to your desktop, sort of like Rainmeter on Windows. Really, though, Conky's pretty simple to get up and running so long as you can find a .conkyrc file for a layout you like; then it's as simple as dropping that file into your home folder.

For Firefox, I haven't played with the customized skinning, really, but custom Firefox themes are considered "Add-Ons," so you should be able to disable or remove them from the Add-Ons screen.

Edit: Ah, cool on Firefox, then. = )

---

### Post by Neoxhadowespio on 2011-04-22
Hmmm, I got the toolbar but I can't find that theme.
I don't like Screenlets...

---

### Post by Copper Bezel on 2011-04-22
Really called a "dock" or "panel"; "toolbar" refers to a row of action buttons near the menu bar in an application.

I don't know about the theme, but the Style (which you set in the General preferences) is Lucido and the icon theme (which you'd have to download separately) is AaOken.

---

### Post by Neoxhadowespio on 2011-05-04
Sorry for the late reply, I was on vacation...

Anyway, I'm gonna settle on Gnome the way it looks, I can do without Conky.
Do you like it...>

[IMG]file:///tmp/moz-screenshot.png[/IMG] [IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=191140&stc=1&d=1304549620[/IMG]

---

