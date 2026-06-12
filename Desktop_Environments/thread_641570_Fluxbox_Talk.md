---
title: "Fluxbox Talk"
date: 2007-12-15
forum: Desktop Environments
---

### Post by -grubby on 2007-12-15
I figured since there was an [openbox]("http://ubuntuforums.org/showthread.php?t=190476&highlight=openbox") EDIT: and an [ICEWM]("http://ubuntuforums.org/showthread.php?t=263710&highlight=icewm") thread, I would make a Fluxbox thread since no one else has done so. I've really recently become a Fluxbox fan, so here is a thread to talk about every aspect of fluxbox

---

### Post by fuscia on 2007-12-15
good choice. i feel like the adam vinatieri of box wm's since i made the switch. for me, there's not that much difference between the two. the right-click menu is much easier to edit, directly, in fluxbox and i like the dragging of windows across workspaces. also, the panel is pretty subtle and useful.

---

### Post by Mateo on 2007-12-15
fluxbox is my favorite lightweight DE.  I'll be using it when i get my ebox 2300.  My only complaint is that the inability to add the menu to the panel makes life hard on Maximize users.

---

### Post by p_quarles on 2007-12-15
Yep. Fluxbox is fantastic. I run it on top of kdm, and have found that it integrates incredibly well with klauncher. Having the KDE app suite without the problems in KWin is a pleasure. 

Plus, having everything configured with plaintext files is something I find very convenient.

EDIT: @mateo: Have you tried making a keyboard shortcut for the menu? That could be your solution.

---

### Post by -grubby on 2007-12-15
> **p_quarles said:**
> Yep. Fluxbox is fantastic. I run it on top of kdm, and have found that it integrates incredibly well with klauncher. Having the KDE app suite without the problems in KWin is a pleasure. 

Plus, having everything configured with plaintext files is something I find very convenient.

EDIT: @mateo: Have you tried making a keyboard shortcut for the menu? That could be your solution.

I use KDM and it works fantastic! And I love the Text-file config files

---

### Post by fedex1993 on 2007-12-15
i use fluxbox on my file server/desktop2. i love it i havnt had much time to customize it because i ahve been ahving problems with my main desktop. I love everything about it i just wish that someway i could intagreate the gnome bar into fluxbox i just still havnt liked the bar in fluxbox. i think i found away with gentoo but i sure someone knows how to

---

### Post by -grubby on 2007-12-15
> **fedex1993 said:**
> i use fluxbox on my file server/desktop2. i love it i havnt had much time to customize it because i ahve been ahving problems with my main desktop. I love everything about it i just wish that someway i could intagreate the gnome bar into fluxbox i just still havnt liked the bar in fluxbox. i think i found away with gentoo but i sure someone knows how to

maybe I'm wrong but you maybe could try running the command :
```
gnome-panel
``` while in fluxbox

---

### Post by -grubby on 2007-12-15
I recently redid my menu, here is the file attached

---

### Post by herbster on 2007-12-15
Yeah we need this thread. I have been using Fluxbox for about 2 weeks now and am loving it. I love how easy the customization is with the menu and keys, etc. It was super easy to finally use my Logitech keyboard multimedia keys, which had been rusting away since I got it. I edited the keys file to have them play, stop, next/prev track in Amarok in a breeze using xev.

I love the flux toolbar. I started disliking pypanel toward the latter time of using Openbox as it would keep flashing and become quite slow with many apps going. Haven't experienced anything of the sort with flux toolbar.

One thing that is bugging me is having certain window attributes remembered. It seems some are remembered just fine via the window menu > Remember, but other ones just keep acting the same way. Gnome-terminal is a real pain in the ***, as for example I prefer having no window decoration on it, but it does not remember this when I open it. I tried editing the apps file and found this:

```
[app] (name=gnome-terminal) (class=Gnome-terminal) (role=gnome-terminal-32198--1957621515-1196728137)
  [Close]	{yes}
```

Through some trial and error, I realized this "(role=)" part is fudging it up. I took that out and it started to remember when I added more attributes, but it recovers this on reboot. Perhaps I must edit it while logged out.

---

### Post by Dixon Bainbridge on 2007-12-15
Flux is my weapon of choice too. I spend most of my time working in it when I'm on the ubuntu box. The tabbed windows feature is a god send.

Anyone running any interesting scripts in their menus?

---

### Post by Onyros on 2007-12-15
Another Flux addict here ;)

Here's what my general [setup]("http://ubuntuforums.org/attachment.php?attachmentid=38683&d=1184931734") looks like...

---

### Post by p_quarles on 2007-12-15
Out of curiosity, is it possible in to set global widget themes in Flux? In KDE, I was able to use the lovely qtcurve widget set for all applications, Gtk and Qt. The KDE apps still use this theme, but Swiftweasel, Miro, GIMP etc. all use a basic Gtk widget set.

---

### Post by -grubby on 2007-12-15
> **p_quarles said:**
> Out of curiosity, is it possible in to set global widget themes in Flux? In KDE, I was able to use the lovely qtcurve widget set for all applications, Gtk and Qt. The KDE apps still use this theme, but Swiftweasel, Miro, GIMP etc. all use a basic Gtk widget set.

you can install gtk-chtheme to change the GTK theme

---

### Post by p_quarles on 2007-12-15
> **nathangrubb said:**
> you can install gtk-chtheme to change the GTK theme
Thanks, nathan, that worked perfectly. That tool allowed me to set GTK apps to use Qt. All is well now. :)

---

### Post by -grubby on 2007-12-15
> **p_quarles said:**
> Thanks, nathan, that worked perfectly. That tool allowed me to set GTK apps to use Qt. All is well now. :)

I know there is an app to change your QT theme if you need to but I can't remember it. I'll post  back when i do
EDIT: Now I've found them:
  qt3-qtconfig (for QT3)
  qt4-qtconfig (for QT4)

---

### Post by -grubby on 2007-12-15
> **nathangrubb said:**
> I know there is an app to change your QT theme if you need to but I can't remember it. I'll post  back when i do
EDIT: Now I've found them:
 qt3-qtconfig (for QT3)
 qt4-qtconfig (for QT4)

what I find strange is that the commands to run them are :
```
qtconfig-qt3
```
```
qtconfig-qt4
```

---

### Post by RedSquirrel on 2007-12-15
> **Mateo said:**
> fluxbox is my favorite lightweight DE.  I'll be using it when i get my ebox 2300.  My only complaint is that the inability to add the menu to the panel makes life hard on Maximize users.

Fluxbox is a WM, not a DE. ;)

You can add the menu to the default toolbar, but you have to edit the source code and compile it. My Howto covers this (see link in my signature) if you want to try it out. A keyboard shortcut is probably a whole lot easier.


Another Fluxbox thread we had going for a while is this one:
[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)

---

### Post by -grubby on 2007-12-15
> **RedSquirrel said:**
> Fluxbox is a WM, not a DE. ;)

You can add the menu to the default toolbar, but you have to edit the source code and compile it. My Howto covers this (see link in my signature) if you want to try it out. A keyboard shortcut is probably a whole lot easier.


Another Fluxbox thread we had going for a while is this one:
[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)

well I couldn't find it searching

---

### Post by p_quarles on 2007-12-16
Dunno if I'm the last Flux user to find this, but this site has a few hundred styles, many of which are quite nice:
[http://www.tenr.de/styles/styles01.php](http://www.tenr.de/styles/styles01.php)

---

### Post by -grubby on 2007-12-16
> **p_quarles said:**
> Dunno if I'm the last Flux user to find this, but this site has a few hundred styles, many of which are quite nice:
[http://www.tenr.de/styles/styles01.php](http://www.tenr.de/styles/styles01.php)

I've never seen that site. Thanks for the link

---

### Post by Onyros on 2007-12-16
> **p_quarles said:**
> Dunno if I'm the last Flux user to find this, but this site has a few hundred styles, many of which are quite nice:
[http://www.tenr.de/styles/styles01.php](http://www.tenr.de/styles/styles01.php)Really, really nice! Thanks for the heads up :D

---

### Post by jviscosi on 2007-12-17
> **Mateo said:**
> fluxbox is my favorite lightweight DE.  I'll be using it when i get my ebox 2300.  My only complaint is that the inability to add the menu to the panel makes life hard on Maximize users.

If you really want an icon in the panel to get your menu, you can try [ftmenu]("http://ftmenu.sourceforge.net/"), which puts an icon in your system tray that displays your Fluxbox menu.  The app has its limitations though, the main one being that it doesn't recurse submenus.  On my machine I modified the code to make it recurse but it still doesn't pick up special Fluxbox commands, and eventually I stopped using it anyway.  Now I use fbpanel instead of the built-in panel, and as others suggested, I have the menu bound to a keystroke.

---

### Post by -grubby on 2007-12-18
ahem *bump*

---

### Post by fedex1993 on 2007-12-19
Yes fluxbox is awsome the only thing i donot like about is the bar for some reason just a personal prefrence. How can i set stuff o be transparent like the bar and everything

---

### Post by herbster on 2007-12-19
You mean the flux toolbar? Man it's the best one I've used!

Transparency is a snap, use the flux menu and in Configuration there's a Transparency menu. Change figures accordingly (255 is opaque, go lower in value for transparency levels).

---

### Post by meborc on 2007-12-19
fluxbox is my secret love (don't tell my gf)

i find flux toolbar the best one yet :) i have set it up just the way i like it - minimalistic (just the things i really need)

screeny [here]("http://ubuntuforums.org/g/images/44655/1_desk1.jpg")

i was a heavy gnome user, never liked kde (i might come to like kde4, but we'll have to see about that)... after gnome started to annoy me i moved to xfce (which i still think is better then gnome or kde)

and then i realised that i need more in less :) fluxbox is what the doctor ordered... what i would like to see is that someone would make a eee pc version of fluxbuntu (there is eeexubuntu already), then i wouldn't have to ponder any more weather to buy one or not :D

---

### Post by -grubby on 2007-12-21
well I betrayed myself and went to XFCE but I miss Fluxbox and as soon as I get my config files set up the way I want them I'm packing and flying to fluxbox land

---

### Post by herbster on 2007-12-22
I had some strange lag in fluxbox, every few seconds a tiny lag that got quite frustrating, so I wiped my ~/.fluxbox and copied back file by file to test, and now it's great. Kinda strange but it's all good now.

---

### Post by corney91 on 2007-12-22
This flux talk is making me want to install it again, now that it's the holidays I can! Yay!

> **Mateo said:**
> fluxbox is my favorite lightweight DE.  I'll be using it when i get my ebox 2300.  My only complaint is that the inability to add the menu to the panel makes life hard on Maximize users.

I had my bar horizontally on the left covering 80%, which allowed me to right click in the bottom right.

---

### Post by fedex1993 on 2007-12-22
Okay i got my fluxbox system working nicely. I still cant seem to beable to get transparency. Also does anyone like have a stock like defualt theme well not stock but like the stock info for themes.

---

### Post by herbster on 2007-12-24
^^^^^ flux menu > configuration > transparency > force pseudo-transparency. Then adjust the alpha values accordingly to what you want (0 = transparent, 255 = opaque).

---

### Post by -grubby on 2007-12-24
for those interested I've made a [fluxbox guide]("http://ubuntuforums.org/showthread.php?t=648036")

---

### Post by K.Mandla on 2007-12-25
In hopes of better organizing all the window manager and desktop environment threads, this has been shifted to Desktop Environments.

---

### Post by -grubby on 2007-12-26
I think tonight I'm going to redo my flux-menu. I just did that with k-menu

---

### Post by -grubby on 2007-12-28
yay! I just made my [first theme]("http://box-look.org/content/show.php/Sunglasses?content=72541") (it's surprisingly easy)

---

### Post by appleshampooid on 2008-01-03
Hi all,

New to Ubuntu, but long-time fluxbox user.  I just set up Ubuntu on my work laptop where I have a docking station.  I'm using xrandr pretty successfully to correctly turn on/off the different displayes and set the resolution when I go from docked->undocked and vice versa.

The only problem is that when I'm docked (resolution 1280x1024), the maximize button maximizes the windows to the resolution of the Laptop's panel (1400x1050), which means I lose a bit of the app off the edges of the screen.

When in this state, xrandr seems to correctly report the resolution and everything:
```

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 3000 x 2000
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right)
LVDS connected (normal left inverted right)
   1400x1050      60.0 +
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

```

Any ideas?

Thanks,
appleshampoo

---

### Post by Blindraven on 2008-01-04
Heres my Fluxtop.
Go [HERE]("http://ubuntuforums.org/g/images/208867/1_Fluxtop.jpg") For a full (much nicer) view.

[IMG]http://ubuntuforums.org/g/images/208867/large/1_Fluxtop.jpg[/IMG]

---

