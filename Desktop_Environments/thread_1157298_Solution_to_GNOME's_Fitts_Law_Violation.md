---
title: "Solution to GNOME's Fitts Law Violation"
date: 2009-05-12
forum: Desktop Environments
---

### Post by unimatrix on 2009-05-12
GNOME violates [Fitt's law]("http://en.wikipedia.org/wiki/Fitts%27s_Law") by placing a panel on the top of the screen by default. There wouldn't be anything wrong with that if maximized windows didn't have their minimize/unmaximize/close buttons placed right beneath the panel.

[IMG]http://img384.imageshack.us/img384/8937/ubuntuclosepoweroff.png[/IMG]

This violates Fitts's law because the user literally needs to aim for the close button on maximized windows, as opposed to how KDE or Windows do this: by putting the window buttons in the absolute screen corner. GNOME's wrong placement greatly reduces productivity (user spends precious time for pointless aiming when closing windows) and causes discomfort in general. On a side note, Mac OS has the same problem.

There are two possible solutions to this problem:
- Remove the upper panel (not really acceptable because it's quite useful)
- **Put the buttons on the panel!**

That is why I have created an applet that does just that.
You may grab it from Gnome-Look: [http://www.gnome-look.org/content/show.php/Window+Buttons+Applet?content=103732]("http://www.gnome-look.org/content/show.php/Window+Buttons+Applet?content=103732")

[IMG]http://www.gnome-look.org/CONTENT/content-pre2/103732-2.png[/IMG]

---

### Post by Fzang on 2009-05-12
I wouldn't mind

I use minimize shortcut on windows 7, mac OS X and Ubuntu

I can see where you're going but how many users actually care about this?

---

### Post by unimatrix on 2009-05-12
It's details like this that make up a better overall user experience. It's why Windows >feels< much more user-friendly. Sorry but it just does. M$ spends lots of money on psychologists and ergonomists to figure out the right placement of stuff. In GNOME this seems to be completely disregarded. It's time the problem gets addressed. Of course this isn't the only such problem, just the most obvious one.

---

### Post by Skripka on 2009-05-12
I have to say, when you are on a small monitor (15" or less, by my tastes)-EVERY pixel freed is good.  GUI space wasted is one of my biggest pet peeves-especially on GUIs that have a toolbar BOTH on the top and bottom.

Good idea on unimatix's part.

---

### Post by Engus on 2009-05-12
I like it, for similar reasons I also moved my taskbar to the side.  Theres plenty of extra room on the sides with a widescreen monitor.

---

### Post by binbash on 2009-05-13
Nice applet BUT this is nothing with that emerald bug.When you max the window 2 times , emerald dissappears.

---

### Post by unimatrix on 2009-05-13
> **binbash said:**
> Nice applet BUT this is nothing with that emerald bug.When you max the window 2 times , emerald dissappears.

Yeah I know. It's a really annoying problem. And it's only made worse by the fact that nobody is working on Emerald anymore. I've tried looking into Emerald's code but I have no clue how to fix this. Just on a side note, here's the error message Emerald produces when it crashes:
> (emerald:6969): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GdkDrawable'
(emerald:6969): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
Segmentation fault

Maybe we can get Emerald fixed somehow? I would require some expert help for that.

Another option is adding a very silly workaround to my applet: restarting Emerald after it crashes. But somehow I doubt Emerald would start fast enough not to be annoying.

If anyone has some ideas/clues on this, please share.

---

### Post by unimatrix on 2009-05-13
Made a bug report for the Emerald bug. I suggest everyone who wants it fixed vote for it.
[https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/376008]("https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/376008")

---

### Post by mcduck on 2009-05-13
> **unimatrix said:**
> It's details like this that make up a better overall user experience. It's why Windows >feels< much more user-friendly. Sorry but it just does. M$ spends lots of money on psychologists and ergonomists to figure out the right placement of stuff. In GNOME this seems to be completely disregarded. It's time the problem gets addressed. Of course this isn't the only such problem, just the most obvious one.

Gnome actually has pretty strict guidelines for human interface design, and they also do lots of research about it. You can read Gnome's human interface guidelines here: [http://library.gnome.org/devel/hig-book/stable/]("http://library.gnome.org/devel/hig-book/stable/")

Also, this design doesn't violate Fitt's law in  any way. This is simply a question of what parts of the desktop the designers see as most important, and therefore which things should get the most easily accessible locations on the screen..

edit: actually Gnome developers seem to think about usability and things like Fitt's law a lot more than Microsoft guys do. For example notice how the menu is placed top left corner, which is the best possible location as it's both easily accessible (corner of the screen) and the first place where people coming from countries where writing goes from left to right, top to bottom, would look at. And all screen corners are put to use while windows only uses two of them (three, if you count in window control buttons on maximized windows)..

---

### Post by coffeecat on 2009-05-13
**unimatrix**, I hate to have to tell you this, but with Windows 7 you can move the taskbar (as they call it) to the top. And very strange it looks there too. :p Or to the left, or the right.

---

### Post by kellemes on 2009-05-13
Nice initiative, I like it a lot.

---

### Post by unimatrix on 2009-05-13
> **coffeecat said:**
> **unimatrix**, I hate to have to tell you this, but with Windows 7 you can move the taskbar (as they call it) to the top. And very strange it looks there too. :p Or to the left, or the right.

I hope you're joking, because this has been possible since at least Win98

---

### Post by binbash on 2009-05-13
> **unimatrix said:**
> I hope you're joking, because this is possible since at least Win98

AHah lol

---

### Post by ugm6hr on 2009-05-13
On whichever Gnome version was included in Ubuntu 8.04. there was a nice applet that defaulted to a "close active window" button, and then changed to a "shutdown menu" button if there were no open windows on the current desktop.

This was a perfect replacement to the default "shutdown menu" button, since it is reasonable to close all active windows before shutting down, and also ensured that the close window button was readily accessible in the top corner.  This also took no extra space when compared to the default Gnome setup.

Unfortunately, in Ubuntu 9.04, Gnome 2.26.1 has gotten rid of this applet in favour of another Window Picker (with a "Close window" button on the active window).  However, because this is a variable size applet, it does not sit well at the top-right corner.

This new applet looks like a good replacement for me, but it is still wider than my previous 8.04 applet, and given I only use a single panel on my space-limited netbook, I'm somewhat limited.

---

### Post by unimatrix on 2009-05-13
> **ugm6hr said:**
> This new applet looks like a good replacement for me, but it is still wider than my previous 8.04 applet, and given I only use a single panel on my space-limited netbook, I'm somewhat limited.

You're free to use thinner pixmaps. Also I could make it possible to select which buttons are there on the panel. Is that what you'd go for?

---

### Post by ugm6hr on 2009-05-13
> **unimatrix said:**
> You're free to use thinner pixmaps. Also I could make it possible to select which buttons are there on the panel. Is that what you'd go for?

I just need the "Close window" button.

I don't find the others to be used often enough to make it worthwhile to have them on the panel.

Thanks for the consideration.

---

### Post by unimatrix on 2009-05-13
> **ugm6hr said:**
> I just need the "Close window" button.

I don't find the others to be used often enough to make it worthwhile to have them on the panel.

Thanks for the consideration.

You're welcome.

OK then, I'll add this feature to the next version.

---

### Post by unimatrix on 2009-05-20
> **ugm6hr said:**
> I just need the "Close window" button.

I don't find the others to be used often enough to make it worthwhile to have them on the panel.

Thanks for the consideration.

Just an update. I've implemented the feature. Get it while it's fresh ;D

---

### Post by ugm6hr on 2009-08-04
Apologies for not responding earlier...

I have since moved my netbook to Xfce, so haven't had a chance to test it.

Still haven't made a final decision re: DE for my main laptop, but might give it a go if I stick with Gnome.

---

### Post by PC_load_letter on 2009-08-04
Personally, I don't care for this problem since I use keyboard shortcuts.
The really annoying problem that could be violating the Fitt's law is when trying to scale the windows, specially sideways or up/down, with the mouse. 

I find it really hard to hunt for the window sides, IMO there should be wider grace region at the borders for capturing the enlargement tool. Yes I know it's easier to use the lower right corner, but sometimes in certain situations one wants to enlarge only one dimension the x or the y, not both.

Any ideas if there are workarounds?

---

### Post by finch127 on 2009-08-04
I think part of the spirit of linux is a little computer savvy nerdiness, and with that comes a little more keyboard and less mouse. I can quickly close firefox with ctrl+w or ctrl+q and most programs have a similar shortcut which is quite useful in that I never click the X button as a carry over from my windows days. I think that perhaps the top bar is not necessary, its just familiar and so it is a good idea to panel integrate them. But then, how would it work if you have nothing open? Would the buttons still stay there? Maybe thats a dumb question but I personally dont like buttons being there and not doing anything for some time.

---

### Post by benerivo on 2009-08-04
And what's the point of window decoration? Surely that is destined to die (EDIT -as finch127 suggests)? I also think the panel is outdated and should be replaced with compiz style screen corners (or other shortcuts). Doing this would benefit small screen users (mobile and netbook).

---

### Post by finch127 on 2009-08-04
Well personally I dont think there is a need for window decoration, maybe just a title bar to the application or something, the same as you have your current panel theme or you could opt to use window decoration to give it a nice border or whatever looks good. I think that perhaps OSX had the right idea when you look at their main panel. Whenever you switch applications, the File/Edit menu changes to reflect the options of the currently open application and when none are open it is a basic start menu. I like this design better because, well it eliminates the need for the program to provide its own File/Edit/History menu and the like, and can save screen real estate as well as having a sleeker appearance. In that case, if you were to add the buttons to the panel as well, you would completely eliminate the need for an application bar. Then if the user still wished, you could still leave the option to change it, or leave a titlebar, or leave window decoration on, etc etc etc. I concur though, we need a more innovative interface.

---

### Post by oerms on 2009-08-20
> **PC_load_letter said:**
> Personally, I don't care for this problem since I use keyboard shortcuts.
The really annoying problem that could be violating the Fitt's law is when trying to scale the windows, specially sideways or up/down, with the mouse. 

I find it really hard to hunt for the window sides, IMO there should be wider grace region at the borders for capturing the enlargement tool. Yes I know it's easier to use the lower right corner, but sometimes in certain situations one wants to enlarge only one dimension the x or the y, not both.

Any ideas if there are workarounds?

Press the alt key, click and hold the middle mouse button and resize the window. Shouldn't be too uncomfortable for you since you use the keyboard for some other shortcuts as you say...

To the applet: Nice work and definitely worth a try to everybody!

---

### Post by eldragon on 2009-08-20
it should be fixed removing the shutdown button. it belongs @ the system menu. where it also appears listed. who shutdowns his computer these days anyway? suspend ftw!

---

### Post by unimatrix on 2009-08-20
> **finch127 said:**
> But then, how would it work if you have nothing open? Would the buttons still stay there? Maybe thats a dumb question but I personally dont like buttons being there and not doing anything for some time.
You can configure it to stay visible or to hide.

---

