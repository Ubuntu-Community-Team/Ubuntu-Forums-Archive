---
title: "Gnome Shell - Change icon size of apps in dock?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by zipmon on 2011-10-15
Hi everybody! Just updated to 11.10 and have set up Gnome Shell, and I'm really enjoying it! :D The only thing that doesn't really work for me is the small size of the application icons in the dock/launcher/favorites bar in the activities overview (see screenshot). It seems like there's a lot of unused space there, and after I open a few apps not on the dock by default, it shrinks the size down even more, and they become quite difficult to hit with the mouse! (I'm on a 1024x600 laptop screen.)

I've actually seen screenshots of other people running Gnome Shell where they look much bigger, relative to the other elements, so that makes me think there must be a way to make them bigger on mine! If anyone has any thoughts, it'd be much appreciated!

Thanks!!
-Morgan

---

### Post by squee on 2011-10-15
I found that the icons get bigger if there are less icons in the dock and smaller when there are more but YMMV

---

### Post by zipmon on 2011-10-15
> **squee said:**
> I found that the icons get bigger if there are less icons in the dock and smaller when there are more but YMMV

Oh definitely - I was just wondering if there was a way to make the initial starting value larger, since I'd like to have around 8 icons up there to begin with. Thanks!

---

### Post by promet on 2011-10-21
I am noticing the same issue. I think it's probably a good idea to have the dock resize itself "auto-magically" with new additions, but I think that it shrinks the icons too drastically, and I'd like to have some (well,* all,* really...) control over this. 

Icons aren't as useful as they are intended to be, i.e. as visual markers for apps/system behaviors, if they are too tiny to interpret, right? An excellent idea, just needs to be further refined, like many things in these new iterations of Ubuntu/Gnome, all due respect.

I tried fooling around with this file, "scale" parameters, etc.:

```
**/usr/share/gnome-shell/extensions/dock@gnome-shell-extensions.gnome.org/extension.js**
``` As, vaguely, recommended by some Archlinux tinkers noted here:

[https://wiki.archlinux.org/index.php/GNOME](https://wiki.archlinux.org/index.php/GNOME)

But, no love...

If anyone has any thoughts, it'd be wonderful. I'm, otherwise, really enjoying gnome shell, but this is, currently, my major "beef" with it. I know it is a flame war level statement to say so these days (hot heads abound), but this sort of base level configuration should be simply implemented ***before*** a major release. I love Gnome Shell and Ubuntu, but I wish the developers would help me love them more; which I am enthusiastic to do!
I pray a peaceful calm upon the waters of Ubuntu/Gnome...

;)

Pies!

[IMG]http://webspace.webring.com/people/qg/galdorf1/pies/pies2.jpg[/IMG]

---

### Post by cbowman57 on 2011-10-21
You might want to look at the dash.js file.

---

### Post by viperdvman on 2011-10-21
I haven't messed with GNOME Shell a whole lot, but all I know is that the more icons you put in the left dash in GNOME Shell, the smaller the icons get to accommodate that space. Other than that, I haven't messed with any settings.

---

### Post by weedwacker on 2011-10-22
I wonder if this is what you are looking for: **CompizConfig Settings Manager**.

Is it installed on your system? If not, you can install from the Software Center. Then, in Dash type in **"Compiz"** and it should come up. Scroll down to the **Desktop** section and on the right is **"Ubuntu Unity Plugin"**. Click on that and you will see three tabs - one of which is named **"Experimental"**. Click and go to the **"Launcher Icon Size"** and use the slider or the up&down buttons to change the icon size.

---

### Post by ShodanjoDM on 2011-10-22
> **weedwacker said:**
> I wonder if this is what you are looking for: **CompizConfig Settings Manager**.

Is it installed on your system? If not, you can install from the Software Center. Then, in Dash type in **"Compiz"** and it should come up. Scroll down to the **Desktop** section and on the right is **"Ubuntu Unity Plugin"**. Click on that and you will see three tabs - one of which is named **"Experimental"**. Click and go to the **"Launcher Icon Size"** and use the slider or the up&down buttons to change the icon size.

This thread is about Gnome-Shell initial icon size in its launcher (dash), and not about Unity. Gnome-Shell is not compatible with Compiz so your suggestion will not work with it.

---

### Post by wgarciamachmar on 2012-03-12
I have the same concern.

---

### Post by Anaximander Thales on 2012-06-07
I'm a little late to this, but replying so that someone else might see the solution.

Install dconf-tools.  Then open Dconf Editor.  In there, go to:
Org -> Gnome -> Shell -> Extensions -> Dock.  

There, you can select size.  Looks like default is 48.  I set mine to 26.  Additionally, in there you can decide which side you'd like the dock on.  On my system, the dock defaulted to the left.  Hated it, so moved it to the right.

---

### Post by zipmon on 2012-06-08
> **Anaximander Thales said:**
> I'm a little late to this, but replying so that someone else might see the solution.

Install dconf-tools.  Then open Dconf Editor.  In there, go to:
Org -> Gnome -> Shell -> Extensions -> Dock.  

There, you can select size.  Looks like default is 48.  I set mine to 26.  Additionally, in there you can decide which side you'd like the dock on.  On my system, the dock defaulted to the left.  Hated it, so moved it to the right.

:)Wonderful!! Thanks so much!!

---

### Post by markbl on 2012-06-08
> **Anaximander Thales said:**
> 
Install dconf-tools.  Then open Dconf Editor.  In there, go to:
Org -> Gnome -> Shell -> Extensions -> Dock.
You guys don't make it clear here but to avoid confusion it should be pointed out that this setting only exists if you install the gnome shell "dock" extension.

---

