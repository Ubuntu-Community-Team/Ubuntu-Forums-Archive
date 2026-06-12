---
title: "Synaptic vs. Add Applications"
date: 2006-03-08
forum: Desktop Environments
---

### Post by th3gh05t on 2006-03-08
Hi, 

Whenever I install programs from the Syanptic Application Manager, the programs never show up the drop-down menu. 

I use the Synaptic program when I can't find a program in "Add Applications".

How do I make it so that the programs I install from Synaptic show up in drop-down menu?

I found out the only way to launch these programs was from a terminal client. (sudo "appname")

Thanks, th3gh05t

---

### Post by aysiu on 2006-03-08
Add Applications and Synaptic are just different interfaces for the same installation process.

If you see an application available in Synaptic, it should be available in Add Applications as well (someone correct me if I'm way off base--this is my understanding of how it works).

That said, a menu item is not always created, even if the application is installed. What applications are you talking about? Are they terminal ones?

---

### Post by th3gh05t on 2006-03-08
[QUOTE=aysiu]What applications are you talking about? Are they terminal ones?[/QUOTE]

There are a few. Just some off the top of my head..

firestarter, airsnort, kismet, etc.

i am sure there are some others..

how would i create a link to open the application on the desktop or any other place for that matter?

---

### Post by white_tiger_daniel on 2006-03-08
Well from my (basic lol) knowledge, synaptic has a helluva lot more packages than add applications, but it's harder to use. Hope I'm right. If I am a big yay for me. \\:D/

---

### Post by Super King on 2006-03-08
[QUOTE=th3gh05t]There are a few. Just some off the top of my head..

firestarter, airsnort, kismet, etc.

i am sure there are some others..

how would i create a link to open the application on the desktop or any other place for that matter?[/QUOTE]

Right-click on any Panel and choose, "Add to Panel." Pick "Custom Application Launcher." Then type in the command for the application (ex: 'gaim' opens up Gaim), and type in the name of the program, and an icon if you want. You can just drag this to the Desktop or leave it on the Panel.

---

### Post by akiro.yamamoto on 2006-03-08
As far as I know, firestarter is available under Applications >> System Tools.
For airsnort you may have to create a .desktop entry for it. Example

---

### Post by akiro.yamamoto on 2006-03-08
You can also create a global .desktop entry manually (I don't know how to create one
graphically) For example:

---

### Post by Madpilot on 2006-03-09
Everything in "Add Applications" will have a menu entry/.desktop file - AFAIK that's the deciding factor in determining what gets in to Add App. Whereas Synaptic has **everything**, including stuff that'll never, ever have a menu entry. (multimedia codecs, Apache, stuff like that.)

Adding menu entries in Ubuntu is dead easy. Right-click on your Applications menu, choose **Edit Menus**.

On the lefthand side of the Menu Editor, pick the category/sub-menu you want your entry to appear in, click on it, then hit the **New Entry** button.

In the New Entry dialogue, fill in the fields - the Command field is the app name that launches it via terminal or Alt+F2; Name is whatever you want; Comment is what you want to appear in the tooltip that appears when you hover over a menu entry.

Hit OK, and you're done!

---

### Post by akiro.yamamoto on 2006-03-09
[QUOTE=Madpilot]Everything in "Add Applications" will have a menu entry/.desktop file - AFAIK that's the deciding factor in determining what gets in to Add App. Whereas Synaptic has **everything**, including stuff that'll never, ever have a menu entry. (multimedia codecs, Apache, stuff like that.)

Adding menu entries in Ubuntu is dead easy. Right-click on your Applications menu, choose **Edit Menus**.

On the lefthand side of the Menu Editor, pick the category/sub-menu you want your entry to appear in, click on it, then hit the **New Entry** button.

In the New Entry dialogue, fill in the fields - the Command field is the app name that launches it via terminal or Alt+F2; Name is whatever you want; Comment is what you want to appear in the tooltip that appears when you hover over a menu entry.

Hit OK, and you're done![/QUOTE]


Yup but these are not GLOBAL they only appear for YOUR user...... well I think that's how it works   :-k

---

### Post by Madpilot on 2006-03-09
[QUOTE=akiro.yamamoto]Yup but these are not GLOBAL they only appear for YOUR user...... well I think that's how it works   :-k[/QUOTE]

Hmm.. I've actually got no idea, this is a one-user computer. I suspect you're correct, though - a customized menu is only customized for that user.

---

### Post by Gustav on 2006-03-09
To edit the application menu just right-click it and choose "edit menu".

Add applications just have a small part of the packages in synaptic. I have the suspicion that all packages that turn up in the menu is in add applications, but that's just a thought :)

---

