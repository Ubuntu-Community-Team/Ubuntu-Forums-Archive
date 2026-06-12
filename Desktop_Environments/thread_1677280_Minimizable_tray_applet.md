---
title: "Minimizable tray applet"
date: 2011-01-28
forum: Desktop Environments
---

### Post by LordDelta on 2011-01-28
I'm using Ubuntu 10.10, Gnome Desktop 2.30.2

Lately, my panel (taskbar) has been getting pretty cluttered.

What I'm specifically looking for is a way to minimize the list of icons in the Notification Area (or alternatively minimize a certain section of my DockbarX application icons).

I'm already using the Dockbar X applet in an attempt to get more space out of my panel. I suppose I could go with the window buttons list applet, but I like Dockbar X better. I also have the default Menu's applet, the Indicator applet 0.3.7, and Notification Area 2.30.2, as well as the Force Quit Applet and the Show Desktop Applet 2.30.2.

Basically, I only have so much space, and about only 13 app spaces (it would be less if I were using the default window lister). Or, when extra stuff goes in my Notification Area/Indicator Applet, it seems to like to load on top of my menus, which is a problem, since I frequently access stuff in my menus (not being fully proficient with solely Alt+F2 commands). I suppose I could help out Dockbar X by fixing this tendency, or write my own option for the Notifcation Area to allow minimization, but I wanted to see if there were already perhaps alternatives out there for this.

If not, I have Quickly installed, so I guess I'll see how much of a headache (or not) that is to use to edit Gnome stuff.

---

### Post by kerry_s on 2011-01-28
have you tried a better dock? awn puts left/right scroll arrows when the dock gets full.

perhaps you need more than 1 panel? :lolflag:

i use awn, i like to separate mine. see pic's

---

### Post by LordDelta on 2011-01-28
Thanks, I actually did try AWN before I used DockbarX.

Firing it up really quickly to check to see if anything had changed while I hadn't been using it, these are my issues with that solution:

[LIST]
[*]I'm not actually a huge fan of Docks. This is coming from someone who used Docks in MacOSX for 2 years (don't get me wrong, OSX is ok, but I don't really like its dock). On the same note, I much prefer the Windows 7 style taskbar.
[*]The applets that come with said Dock (that is AWN), don't seem to offer the same functionality as my Panels. There are no menus, it doesn't seem like it has the same taskbar/system tray functionality that Panels does.
[*]I suppose I might be able to find applets for AWN to replace the applets I'm using in the Gnome-panel, but afaik AWN isn't managed by the Gnome Desktop, and so I doubt upgrading said applets would actually be handled for me.
[*]Despite not liking OSX-style docks that much, I'm actually something of a minimalist, and I don't appreciate having two panels. I appreciate being able to take in what desktop programs I'm running at one sweep, as well as any relevant status indicators.
[*]I also really enjoy the window previews that DockbarX can offer (with relative success), which I don't think AWN has either.
[*]Finally, none of this actually answers my question, which is that I'm looking for a minimizable status tray for the gnome panel, if such a thing exists.
[/LIST]

---

### Post by kerry_s on 2011-01-28
try using a drawer, you can put any gnome panel applet in a drawer.

try awn ppa version that's the 1 i'm using.

awn has all the indicators, i just don't use all of them.
compiz does the previews
awn can be a panel to

awn is built to replace gnome-panel, so it just comes down to your fear of docks or using the right tool for the job.

---

### Post by Krytarik on 2011-01-28
@kerry_s: I also tried AWN recently, and I would really be happy to replace both Gnome Panels with it.

But there is a bug currently: If you have enabled autofocus on mouse-over in Compiz' settings, you can't select an item from the grouped windows list, since AWN looses focus before, [https://bugs.launchpad.net/awn/+bug/500981](https://bugs.launchpad.net/awn/+bug/500981) . Is that working at your machine? 

And how did you get those dialog boxes for the indicator applet, what do you mean by "drawer"?

I would like do have gnome panel's System Monitor applet in the upper right dock (like the one you have), since it also offers to monitor the RAM and is otherwise more stable than the system monitor applet provided by AWN. Is that achievable by such a "drawer"?

---

### Post by kerry_s on 2011-01-28
i can't find that focus setting your talking about. see pic

> And how did you get those dialog boxes for the indicator applet

thats awn to.

the drawer is in gnome-panel applets, not awn.

no, you can't use gnome applets in awn. i would suggest a auto hiding gnome-panel with just those must have gnome applets.

do you have some kind of ram/memory problem you need to monitor?

i'm old school, long past worrying about what the computers doing, just let it do it's thing & i just use it. :lolflag:

---

### Post by Krytarik on 2011-01-28
> **kerry_s said:**
> i can't find that focus setting your talking about. see pic

It's in "General Options -> Focus & Raise Behaviour", it's called "Click To Focus". If you uncheck it, the window the mouse is over gets the focus, otherwise you would have i.e. to click the window of a web browser after clicking an URL in a mail before, to loose it's "demandsattention" state, meaning stops blinking/beeing highlighted.

Indicators: Ok, then I've overlooked that applet.
> **kerry_s said:**
> 
do you have some kind of ram/memory problem you need to monitor?

No, everything is fine. But since I'm using a 9-year-old computer, I have to keep an eye on CPU/RAM usage. CPU usage is usually low, unless I watch videos/TV or of course run flash content. But RAM usage is usually at ca. 50%, I only have 1,2 GB, although I even already upgraded ca. one year ago. I could install 2 GB at maximum, but I don't really see the need. I think I generaly like to know, how much resources are used. Recently I caused an infinite loop at something, don't remember, and memory usage just *jumped up*:P, to know how fast you have to act in such cases really helps to prevent a crash or something even more serious.

---

### Post by kerry_s on 2011-01-28
> It's in "General Options -> Focus & Raise Behaviour", it's called "Click To Focus".

yeap, that bug is still there.

---

### Post by Krytarik on 2011-01-29
@kerry_s: Thanks for confirming. I tried AWN just some days ago. But I somewhat hoped that the bug doesn't affect all, thus would be somehow fixable by the user, because it seems that the developers themself haven't done anything about it so far.

@LordDelta: To get back to your original topic. Following the listing in your initial post, I'm not really sure what you have already removed. I'll list what is removeable, and how:

indicator-me: remove package
indicator-sound: remove package
indicator-messages: remove from panel
Network Manager: disable in "System -> Preferences -> Startup Applications"
indicator-session: remove from panel

---

### Post by LordDelta on 2011-01-29
@Kyatarik: I haven't removed any of those.

@kerry_s: Just to clarify I had to upgrade to the awn*trunk packages to access that indicator applet, as per the following command:

```
sudo add-apt-repository ppa:awn-testing/ppa && sudo apt-get update
sudo apt-get install avant-window-navigator-trunk awn-applets-c-core-trunk awn-applets-c-extras-trunk awn-applets-python-core-trunk awn-applets-python-extras-trunk
```

I'm not "afraid" of docks, they just can't do enough for me, too simple stupid for my tastes. Yeah, awn is great, but its not what I want.

Also, I noticed since awn requires compiz fusion (at least on my platform), that means it requires a graphics card? Not so great for older users, and also probably not so great I bet for my battery life. I have a graphics card, I do use fusion, but requiring a section of my hardware that acts like a power hog to run my OS doesn't sound like a great idea? I'm not sure on this though....anyways I think DockbarX uses fusion too, so this is a moot point to this discussion, but replacing gnome-panel with awn doesn't sound like the best thought out plan ever.

I noticed the fact that DockbarX can be included inside AWN, which looks promising:

[http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)

I think I'll tinker around this weekend and see what I can get done in the way of improving awn/dockbarx.

---

### Post by Krytarik on 2011-01-29
> **LordDelta said:**
> @Kyatarik: I haven't removed any of those.

Do you really need indicator-me then, aka "social networking thingy";)? Removing that alone saves a lot of panel space. See the attached image how my tray looks currently.

---

### Post by LordDelta on 2011-01-29
@Krytarik Hmm, I'll look into it. At any rate this whole menu system on ubuntu is due for a large overhaul anyways....and actually I seem to find it usefull...to the extent that I do most of my networking via IM, and email, and a bit of status update via twitter (i.e. gwibber is usefull). But yeah, I could probably just stick those things in a drawer I suppose...

EDIT: oops, I meant the indicator-messaging, not the indicator-me, don't use that one anyhow! :lolflag:

---

### Post by Krytarik on 2011-01-29
> **LordDelta said:**
> @Krytarik Hmm, I'll look into it. At any rate this whole menu system on ubuntu is due for a large overhaul anyways....and actually I seem to find it usefull...to the extent that I do most of my networking via IM, and email, and a bit of status update via twitter (i.e. gwibber is usefull). But yeah, I could probably just stick those things in a drawer I suppose...
I also find indicator-me somewhat usefull, to easyly/fast change your status. But in the end, *blasting* the tray area that hefty just for that is a bit high price, I find. I removed it just recently. And of the other usual items, I don't use them at all usually.

---

