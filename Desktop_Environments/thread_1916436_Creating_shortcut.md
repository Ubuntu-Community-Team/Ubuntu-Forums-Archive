---
title: "Creating shortcut"
date: 2012-01-28
forum: Desktop Environments
---

### Post by gaward on 2012-01-28
Hi,

I have been a bit of an advocate for Ubuntu (and Linux in general) for some time now. However recently I have come across some decisions that make absolutely no sense to me at all. Apparently something as simple as creating a shortcut on your desktop is no longer permissible.

I have tried in vain to create a shortcut for an application that I have installed on my machine, buried about 6 levels deep in the directory structure. On my work PC (being a Windows based machine) it would be a simple case of right click and select "send to desktop as shortcut". Done. Simple! However for what must be the most bizarre rationale, it has been decided this should not be the case for Ubuntu anymore.

Note that making a copy of the file I am trying to run, and pasting to the desktop does not work! The app needs to be run from the directory where it is installed. I have read of a process on the internet to "Create Launcher" which does not work on my machine, either in the terminal window, or the ALT + F2 option. And this seems a ridiculously complex procedure for what used to be a very straight forward process.

This decision to do away with short cuts amazes me, as this is a key advantage of using a GUI in the first place! What about when people want to create a shortcut to folders too.

I am hoping this is little more then a serious oversight by the Ubuntu team, and soon to be sorted before it gives "pro Windows" users further justification for staying away from Linux. In the mean time, I will have to continue storing my shortcut in my head until this flaw is rectified.

---

### Post by jerrrys on 2012-01-29
This must be something unique to Unity.  Creating a link and dragging it to the desktop works for me.

---

### Post by mcduck on 2012-01-29
> **gaward said:**
> Hi,

I have been a bit of an advocate for Ubuntu (and Linux in general) for some time now. However recently I have come across some decisions that make absolutely no sense to me at all. Apparently something as simple as creating a shortcut on your desktop is no longer permissible.

I have tried in vain to create a shortcut for an application that I have installed on my machine, buried about 6 levels deep in the directory structure. On my work PC (being a Windows based machine) it would be a simple case of right click and select "send to desktop as shortcut". Done. Simple! However for what must be the most bizarre rationale, it has been decided this should not be the case for Ubuntu anymore.

Note that making a copy of the file I am trying to run, and pasting to the desktop does not work! The app needs to be run from the directory where it is installed. I have read of a process on the internet to "Create Launcher" which does not work on my machine, either in the terminal window, or the ALT + F2 option. And this seems a ridiculously complex procedure for what used to be a very straight forward process.

This decision to do away with short cuts amazes me, as this is a key advantage of using a GUI in the first place! What about when people want to create a shortcut to folders too.

I am hoping this is little more then a serious oversight by the Ubuntu team, and soon to be sorted before it gives "pro Windows" users further justification for staying away from Linux. In the mean time, I will have to continue storing my shortcut in my head until this flaw is rectified.
First, the decision to remove the "Create Launcher" option from the right-click menu was not done by Ubuntu developers, and is in no way related to Unity. It was done by Gnome developers, as Gnome Shell doesn't use desktop icons by default and such option would, from their point of view, be useless.

Anyway, you can very easily create launchers using the very same tool that has been available in all the previous Ubuntu versions, Alacarte (appears as "Main Menu" in the menus).

And if you want a link instead, that's as simple as dragging a file somewhere using middle mouse button and selecting "Link Here".

...also you are constantly talking about "shortcut", so I'd want to confirm which one you actually want, a launcher or a link? The Windows concept of "shortcut" would, depending on the situation, fit both these concepts (and at the same time without having the power of either a launcher or a link :D).

---

### Post by tlcstat on 2012-01-29
Greetings,
Some links need permissions. If you want a launcher on your Desktop ...example ...firefox..in a terminal type sudo nautilus/file system/usr/share/applications/ and drag the firefox launcher onto your desktop. I also agree with the previous post.The word Link is kind of a broad term in Linux that doesn't explain what you are trying to do. As a previous Windows user I can tell you that Linux is most definitely different. No complaints here!
tlcstat

---

### Post by mcduck on 2012-01-29
> **tlcstat said:**
> Greetings,
Some links need permissions. If you want a launcher on your Desktop ...example ...firefox..in a terminal type sudo nautilus then from the window browse for  /file system/usr/share/applications/ and drag the firefox launcher onto your desktop. I also agree with the previous post.The word Link is kind of a broad term in Linux that doesn't explain what you are trying to do. As a previous Windows user I can tell you that Linux is most definitely different. No complaints here!
tlcstat
Actually you shouldn't link any program to your desktop that way. That would make the launcher owned by root, which is completely unnecessary and would only make dealing with the launcher a lot harder.

If you want a desktop icon for a program that's already in your menu, all you need to do is drag&drop it from the Dash menu to your desktop.

...and even if you wanted to do it by copying the .desktop file from /usr/share/applications, you could perfectly well do that without root permissions. You already have the right to read from that directory, and to write to your own desktop.

---

### Post by tlcstat on 2012-01-29
Greetings,
In addition to my previous post I should say that Linux in general will make you jump through some hoops to get something done in order to verify that you really want to do it. This tightness can be confusing and restrictive to someone new to Linux. If you are above par in Windows you should be pretty good in Linux in no time. Just have to learn the rules.
tlcstat
+

Greetings,
original by mcduck
> Actually you shouldn't link any program to your desktop that way. That would make the launcher owned by root, which is completely unnecessary and would only make dealing with the launcher a lot harder.

There you go! Hoops and rules. 
tlcstat

---

### Post by gaward on 2012-02-01
I want to thank all of you for your fast assistance. Yes, I still consider myself a practical newbie to Linux, even though I have been running Ubuntu (exclusively) on my home PC for a little over a year now. I still spend the majority of my time using windows at work, however I have been through several upgrades and fixes with Ubuntu since I started more than a year ago.

I use my machine for a broad range of applications, everything from listening to music, spreadsheets, CAD, web browsing etc. and have had minimal problems with the machine. It shows how little I know when I cannot differentiate between Ubuntu and Gnome. I have heard of Gnome many times, however I presumed this to be a different "flavour" of Linux, not something Ubuntu builds upon.

You say a Windows link is a very broad term, sorry I don't understand. To me it's very simple. A shortcut simply jumpts to wherever an application is located in your directory structure and executes that application/opens picture/plays song etc. It's as if the directory where the item in question is stored, is actually part of the desktop itself. IE it executes exactly as if you had double clicked on the application etc. itself. Seems cut and dry to me.

I will try some of your suggestions and see how they go, again thanks for the assistance. I hope nobody took my rant to heart, however I get very frustrated when it appears someone has taken something as simple as shortcut generation and done away with it without just cause. If Gnome no longer requires it, why? What's their alternative?

I have heard there are Japanese people who still use an Abacus in favour of an electronic calculator, and can "out calculate" the average person using it. I strongly doubt this is therefore justification for us all to be using an Abacus over a calculator! Food for thought...

---

### Post by tlcstat on 2012-02-01
-
Greetings, 
Hopefully you got a link to work. In the beginning of this OS's history was the phrase "GNU's not Unix". This sums it all up for me and I think if you Google the term you will get an understanding of what you are dealing with. Linux is neither a calculator nor an abacus. It starts with a vanilla kernel [or not] and becomes what ever the developer wants it to be. The big thing that makes it different is that it is open source and you can code your own darned link if you care to. You can even invent your own name for it! Some countries even have their own distinct national version of Linux. It just seems to me that both the calculator and the abacus has some unresolved issues that the computer tries to overcome. But even that attempt made this forum necessary as well as M$'s repository of hundreds of thousands of service bulletins and daily security fixes. 
tlcstat

---

### Post by mcduck on 2012-02-01
> **gaward said:**
> I want to thank all of you for your fast assistance. Yes, I still consider myself a practical newbie to Linux, even though I have been running Ubuntu (exclusively) on my home PC for a little over a year now. I still spend the majority of my time using windows at work, however I have been through several upgrades and fixes with Ubuntu since I started more than a year ago.

I use my machine for a broad range of applications, everything from listening to music, spreadsheets, CAD, web browsing etc. and have had minimal problems with the machine. It shows how little I know when I cannot differentiate between Ubuntu and Gnome. I have heard of Gnome many times, however I presumed this to be a different "flavour" of Linux, not something Ubuntu builds upon.

You say a Windows link is a very broad term, sorry I don't understand. To me it's very simple. A shortcut simply jumpts to wherever an application is located in your directory structure and executes that application/opens picture/plays song etc. It's as if the directory where the item in question is stored, is actually part of the desktop itself. IE it executes exactly as if you had double clicked on the application etc. itself. Seems cut and dry to me.

I will try some of your suggestions and see how they go, again thanks for the assistance. I hope nobody took my rant to heart, however I get very frustrated when it appears someone has taken something as simple as shortcut generation and done away with it without just cause. If Gnome no longer requires it, why? What's their alternative?

I have heard there are Japanese people who still use an Abacus in favour of an electronic calculator, and can "out calculate" the average person using it. I strongly doubt this is therefore justification for us all to be using an Abacus over a calculator! Food for thought...

Well, the difference to shortcuts in WIndpows is that Linux actually has two very different concepts, a link and a launcher.

A launcher is what you'd use to start an application. It has an icon, a description of what the program n question is and does (perhaps in multiple languages), and other that kind of information.

...and a link is something that works on a deeper level of the system, a feature of the filesystem itself, making a file or a directory appear in many places in the filesystem. And, unlike a windows shortcut that takes you to another location, a link does the opposite, it brings the target to where the link is. 

For example if you have a shortcut to "C:/Program Files" on your windows desktop, clicking it would take you to "C:/Program Files". On the other hand, if you have a link to "/usr/bin" on your Linux desktop, clicking it would take you to "~/Desktop/bin" (which would be exactly the same directory as /usr/bin, only available in the different location because of the link. (and being a feature of the filesystem, not the user interface, links work for all the programs, and not just for the user like Windows shortcuts do).

Latest windows versions actually have added support for this kind of links, although they still lack any means for the user to create and manage them from the graphical interface, leaving them more as a rarely used expert feature.

Since both these concepts would somewhat fit the idea of a "shortcut", you really need to know yourself which functionality is what you are after. If it's starting a program, you want a launcher. And if it's a question of file management and organizing and modifying directory hierarchy to fit your needs, you want a link instead. (and asking a Linux user about "shortcut" would just be confusing as there is no direct equivalent as the windows shortcut, instead you have these two quite different, but also more powerful systems)


Edit: so there is and never has been an direct equivalent of a shortcut on Linux. And like I said Gnome 3 has no need for Launchers on Desktop as there is no desktop on Gnome 3. Launchers in *menus* work just like before, and can be created and managed using the same tools as before. (and even desktop launchers are possible, assuming you've enabled the desktop icons yourself all you need to drag&drop one from the menu to desktop.)

---

### Post by gaward on 2012-03-27
Thanks for all the help and advice guys. Obviously there is a lot more for me to still learn about Ubuntu/Linux. Overall I continue to enjoy the experience and appreciate the work that many people have put into making Ubuntu such a success. Thanks again.

---

