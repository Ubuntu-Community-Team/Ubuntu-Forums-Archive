---
title: "Edit the right click menu"
date: 2013-04-13
forum: Desktop Environments
---

### Post by politenessman on 2013-04-13
There have been a few threads with this and similar titles, but they don't give me what I am looking for.
I want to edit the right click menu, but NOT the application sub menu.

As it stands now, the applications sub menu is at the bottom of the main menu. Give that the applications menu is the one I use most, I'd like to be able to shift it to the top, or even completely edit the main menu to be the applications menu, with the (current) main menu being the sub menu (that made sense when I wrote it, if its not clear I'll try and explain further)

The various edit tools out there (and I do have them installed) only enable me to edit the applications menu, but not the main menu.

How do I edit the main menu?

---

### Post by Frogs Hair on 2013-04-13
The desktop context menu is usually controlled by the file manager and there are possible custom actions . [http://docs.xfce.org/xfce/thunar/custom-actions](http://docs.xfce.org/xfce/thunar/custom-actions)

---

### Post by politenessman on 2013-04-13
Thanks but I'm not looking to add more functions to the file manager. I just want to edit the right click menu

---

### Post by Frogs Hair on 2013-04-13
As I wrote the desktop right click/context menu is a fuction of the file manager and not the main menu as you have discovered.

---

### Post by politenessman on 2013-04-13
I must be missing something in my understanding then. The menu I get when I right click in Thunar is not the same as the menu I get when I right click on the desktop.

---

### Post by Frogs Hair on 2013-04-13
The file manager handles the desktop. Below is the context menu I was writing about.

---

### Post by politenessman on 2013-04-13
Yep, thats the menu I want to edit. I notice you don't have 'applications' option turned on. Its the applications option I want to move - either that or I add some of my favorite applications to the menu you pictured.
I'm guessing at this time, I can't do that?

---

### Post by politenessman on 2013-04-13
So I've been playing a little with Thunar, and found that I can add applications to the menu using the 'Configure Custom Actions', BUT, they only appear when Thunar is open. If you right click on the desktop they do not appear in the menu and no amount of messing with the 'Appearance Conditions' tab will change this. There must be a way of editing the Thunar menu, I guess I just need to keep looking.

---

### Post by Frogs Hair on 2013-04-13
The link describes one way of going about it.

---

### Post by Morbius1 on 2013-04-13
This might be helpfull.

This is what you see when you right click the desktop on an XFCE desktop:
[ATTACH=CONFIG]241302[/ATTACH]
I personally don't know how to move the "Applications" part of it and I'm not sure you can modify the Applications part itself without changing the one in the Menu button. But try to change the main Menu and see if it is reflected in the right click menu:

Right Click the Menu button "Applications Menu" on the panel > Properties > Edit Menu

---

### Post by politenessman on 2013-04-13
> **Frogs Hair said:**
> The link describes one way of going about it.

Again, I must be missing something because I'm not seeing it. 
I can pull up Chrome all day from withing Thunar by right clicking now, but right clicking on the desktop causes that option to disappear.

This is my right click menu (right clicking on the desk top)
[[IMG]http://i86.photobucket.com/albums/k115/politenessman/th_nowyoudont_zps7fc72630.jpg[/IMG]](http://s86.photobucket.com/user/politenessman/media/nowyoudont_zps7fc72630.jpg.html)

And in Thunar, there is Chrome - 
[[IMG]http://i86.photobucket.com/albums/k115/politenessman/th_Nowyouseeit_zps49567f1d.jpg[/IMG]](http://s86.photobucket.com/user/politenessman/media/Nowyouseeit_zps49567f1d.jpg.html)

There has to be a way for Chrome to appear when right clicking on the desktop, but I just can't figure it out.
Notice the 'Open Terminal Here' option is always there .....I use the same settings for Chrome. Odd......

---

### Post by politenessman on 2013-04-13
> **Morbius1 said:**
> This might be helpfull.

This is what you see when you right click the desktop on an XFCE desktop:
[ATTACH=CONFIG]241302[/ATTACH]
I personally don't know how to move the "Applications" part of it and I'm not sure you can modify the Applications part itself without changing the one in the Menu button. But try to change the main Menu and see if it is reflected in the right click menu:

Right Click the Menu button "Applications Menu" on the panel > Properties > Edit Menu

Applications and the menu button are the same menu - if you change one, the change is reflected in the other. The problem is that editing the applications menu has no bearing on the top level menu, and its that menu that I want to edit.

---

### Post by Merrattic on 2013-04-13
Have you tried:

Settings > Settings Manager > Desktop > Icons > Icon Type = None

This removes a lot of stuff from the right click desktop menu leaving "just" applications, with a very similar look to the Applications Menu

(You do lose desktop icons in the process)

You can then use alacarte  (Settings > Main Menu) to edit both, IIRC.

---

### Post by Toz on 2013-04-13
The Chrome entry from within Thunar is a custom action (Thunar->Edit->Configure Custom Actions).

Another app, xfdesktop, manages the desktop. There has been some talk of having Thunar also manage the desktop, but that hasn't happened yet.

The right-click "context menu" (when right-clicking on the desktop) is not currently editable - it is hard-coded into the application.

You can hide the display of the desktop "context menu" by following the instructions just posted by Merrattic.

---

### Post by Frogs Hair on 2013-04-13
> [COLOR=#000000]There has been some talk of having Thunar also manage the desktop, but that hasn't happened yet.[/COLOR]

Thanks Toz, I use XFCE and am used to having Nautilus handle the desktop in gnome. Because custom actions are possible in the desktop context menu  I thought Thunar was handling the desktop  . The custom action like open terminal what I thought the OP was looking for.

---

### Post by politenessman on 2013-04-14
Interestingly enough, after a reboot, my new custom actions did appear when right clicking on the desktop.
I might play with that to see if I can create a custom action, triggering the applications menu, so I can effectively relocate the menu item on the root menu.

Frankly I am amazed the root menu is not editable, given how editable everything else is.

> The custom action like open terminal what I thought the OP was looking for.
I'm sorry, I guess I didn't do a very good job of explaining the problem.

---

### Post by Merrattic on 2013-04-14
> **politenessman said:**
> Interestingly enough, after a reboot, my new custom actions did appear when right clicking on the desktop.

I don't believe that :? Custom actions only work inside Thunar, they are in no way related to the desktop? Prepared to be proven wrong though ;)

> **politenessman said:**
> Frankly I am amazed the root menu is not editable, given how editable everything else is.

It is, as I explained further up, but perhaps not to the extent you want.....:KS

---

### Post by politenessman on 2013-04-14
> **Merrattic said:**
> I don't believe that :? Custom actions only work inside Thunar, they are in no way related to the desktop? Prepared to be proven wrong though ;)



It is, as I explained further up, but perhaps not to the extent you want.....:KS

Challenge Accepted :)
[[IMG]http://i86.photobucket.com/albums/k115/politenessman/th_ChallengeAccepted_zpsfbdc5cdb.png[/IMG]](http://s86.photobucket.com/user/politenessman/media/ChallengeAccepted_zpsfbdc5cdb.png.html)
I can run Leafpad and Chrome from the desktop, the file delete also works. I am however having trouble with the application menu, so far that does not work, but I will work on that over the next week or so.

---

### Post by Merrattic on 2013-04-15
:( Challenge defeated ;)

Yes, if Settings>Desktop>Icons>Icon type = File/launcher Icons

then custom actions for correct conditions show up. Interesting mix of xfdesktop and thunar :)

You'll be installing openbox next :D

---

### Post by klein5366 on 2013-04-20
hi 
after looking through countless threads on this subject i found on xfaces Q.A. page where they said the right click menu was compiled into the desktop when it is compiled and the applications menu 
is the only menu you can edit. so on that note i started looking at alternatives i made a python button menu witch is just a window with buttons, mine runs a couple scripts, one opens a web page in firefox or a new tab,  when i want to open my script.py i use keyboard short cut <super>x and it pops up in the center of my screen if there is any interest in this i will post what i have.

---

### Post by thesoundman20 on 2013-06-17
so i have looked and looked and this is the only thread that talked about this specifically. klein5366, politenessman am i to understand that you can NOT edit the context menu in xubuntu? and that only the applications menu is editable? 

if the applications menu is editable is it possible to add a launcher to the applications menu that runs a script? i apologize if im bumping and old thread but im trying to accomplish the same thing as politenessman and edit my context menu.

---

