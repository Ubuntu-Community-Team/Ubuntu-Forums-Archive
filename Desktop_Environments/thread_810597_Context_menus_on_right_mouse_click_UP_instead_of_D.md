---
title: "Context menus on right mouse click UP instead of DOWN?"
date: 2008-05-28
forum: Desktop Environments
---

### Post by tarsius4 on 2008-05-28
Hi everyone,

I'm looking for a way to configure gnome to display context menus after I release the right mouse button instead of as soon as I push the button.

Problem: In firefox, I often find myself clicking and releasing the right mouse button to select an option in the context menu.  At the same time, I move the mouse toward the area where I expect the menu to appear.  Under my default gnome configuration, releasing the right mouse button automatically selects an option on the context menu as soon as it appears.

I use Windows often and have the habit of expecting the menu to appear after I release the right mouse button.  There is no way to configure this behavior in Ubuntu's System>Preferences>Mouse. Does anyone know how to get this behavior?

Thanks

---

### Post by tarsius4 on 2008-05-29
bump (1 of 3)

---

### Post by tarsius4 on 2008-06-03
bump 2/3

---

### Post by ChillMonkey on 2008-06-03
> **tarsius4 said:**
> Hi everyone,

I'm looking for a way to configure gnome to display context menus after I release the right mouse button instead of as soon as I push the button.

Problem: In firefox, I often find myself clicking and releasing the right mouse button to select an option in the context menu.  At the same time, I move the mouse toward the area where I expect the menu to appear.  Under my default gnome configuration, releasing the right mouse button automatically selects an option on the context menu as soon as it appears.

I use Windows often and have the habit of expecting the menu to appear after I release the right mouse button.  There is no way to configure this behavior in Ubuntu's System>Preferences>Mouse. Does anyone know how to get this behavior?

Thanks

Not sure exactly what your issue is. I have no problems with the right-click context menu and my gnome-settings are the defaults.

In firefox, if I click and release the right mouse button, my menu pops up. It stays until I click an item on the list or click the right mouse button again. 

sounds like that is the behavior you are looking for. what are your options under System > Preferences > Mouse, set to?

---

### Post by tarsius4 on 2008-06-03
```

Current Behavior:

--->right mouse down--->right mouse up
    ^menu appears       ^menu item selected

Desired Behavior:

right mouse down-->right mouse up-->right mouse down-->right mouse up
                   ^menu appears                       ^menu item selected

```

The problem is that I tend to quickly click and release, expecting the context menu to appear.  Often the menu appears beneath the cursor and a menu option is immediately selected before the menu is even rendered. So in firefox, there is a tendency for "Switch Page Direction" to immediately be selected.

This is a major annoyance as it happens frequently throughout the day. Windows XP exhibits the desired behavior... I would like to configure GNOME to act consistent with my experience in XP.

---

### Post by putteb on 2008-12-26
I'm having the exact same problem. I would like the right click to be triggered when I release the butten instead of when I press it.

Have you solved the problem? I have been searching without finding any solution.

---

### Post by tarsius4 on 2008-12-27
I've been looking for a solution for a while, but I have come to believe that GNOME is just not especially customizable to favor simplicity.  If there were an abundance of options, it might be too overwhelming.  My guess is that the real "solution" is to use a different desktop environment if you want more options.  I've also gradually gotten more used to the right-click behavior, so I've decided just to live with it.

Wikipedia has a good article on desktop environments: [http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

---

### Post by Zorael on 2008-12-30
Subscribing for interest; this is the case in KDE as well. Would love to find an easy xorg.conf option or xserver-xorg-input-mouse replacement for this.

---

### Post by jfrorie on 2009-01-22
I don't see any way to do it and I've looked for more than a year.  Glas to see there are others.  I'm going to submit it as a feature enhancment.  My thinking is that I'm going to get savaged for suggesting it.  I sure could use some support.  

The report is at:

[https://bugs.launchpad.net/ubuntu/+bug/320259](https://bugs.launchpad.net/ubuntu/+bug/320259)

---

### Post by tarsius4 on 2009-01-28
Thanks for posting the bug report, jfrorie. Hopefully we'll soon be able to reconfigure this minor nuisance.

---

### Post by rabarberski on 2009-02-05
I am not entirely sure if the issue I am having is the same as described above, but I think so. 
For me, the exact issue is that when I right-click (e.g. on the Desktop) the first item is selected in the pop-up menu. So if you release the button, that action is executed. Very annoying.

This issue is also described [here]("http://www.mail-archive.com/nautilus-list@gnome.org/msg04298.html") :

> In some apps, the right-click contextual menu
appears with its first item selected by default. If you release the
right button, the first item is chosen.

This seems contrary to the behavior in some - but not all - other Gnome
apps, where the contextual menu appears with no item selected. In those
apps, releasing the right mouse button leaves the menu open but doesn't
execute an option.

Even worse, if the menu is near the bottom of the screen, the *last*
item is selected, since the menu appears anchored to the lower-left
corner instead of the usual upper-left corner. And that doesn't always
seem to be automatically executed on mouse release (contrary to the
first item, which always seems to be executed).

So you're not ever sure what will happen if you click and release the
right button without moving the mouse: select item 1 + execute, select
item n + execute, select item n + no execute, no item selected + menu
remains, ...


I have been experiencing this from about Ubuntu 8.04 which I have been running under Parallels on Mac. Not sure if it is an Ubuntu only issue, or cause by running this virtually...

---

### Post by jfrorie on 2009-02-05
That's an interesting thread.

The problem you describe is related to the issue.  It points out an additional related problem that I've been having, but was unable to figure it out.  I'm not crazy.  Thanks!

Jim

---

### Post by cobaltinfinity on 2009-02-07
The right click on my mouse often goes crazy when using Ubuntu. For instance, on Firefox I sometimes right click a url to open it in a new tab, and before I know it I have inadvertently selected 'send link' and a mail document opens up. 

I thought I was just being careless but maybe there is a configuration issue.

---

### Post by bogdan.c on 2009-05-15
As a new Ubuntu user I find this issue really annoying sometimes. I hope there is at least a way to ensure that the context menu will never pop-up under the mouse pointer.

With some mouse devices you really need a steady hand, as right-clicking and slightly moving the pointer before releasing will activate the first entry on the context menu.

---

### Post by maandverband on 2010-03-19
This bug is driving me insane, but unfortunately they won't give us an option to configure this behavior to show the context menu on right mouse click up.

---

### Post by sharq1 on 2011-03-16
Is there going to be fix for this? Not necessarily changing method to click when mouse DOWN (click on mouse UP is standard), but for example by ignoring first mouse UP?

---

### Post by tarsius4 on 2011-03-17
No fix that I'm aware of... As you can see, this was an old thread, so in the past three years I've just gotten used to the GNOME clicking behavior :-/  However, I still believe this option should be exposed for user customization.

---

