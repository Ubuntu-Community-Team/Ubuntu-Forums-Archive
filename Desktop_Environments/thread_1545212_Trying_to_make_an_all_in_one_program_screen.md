---
title: "Trying to make an all in one program screen"
date: 2010-08-03
forum: Desktop Environments
---

### Post by rakarnsunju on 2010-08-03
Hello all
 
Im trying to make an all in one program splash screen for ubuntu.
 
the idea behind this is, I have alot of staff at my store who will be using a system system for a few programs, but almost none of them have any real use of ubuntu.
 
What I would like to do is have them log in and instead of seeing the desktop have a splash screen pop up with the program choices they can use, all in one place.
 
Alas i have no idea on how to do this, but Im very willing to learn.
 
Any Idea's?
 
Ra.

---

### Post by stderr on 2010-08-03
Hi Ra

I should prefix this by saying I don't know if similar software projects already exist out there that you could use.

In terms of creating it, it rather depends on what programming languages (if any) you're familiar with, as it would make sense to use those sofar as possible. It also depends what you want the interface to look like. 

If you want a graphical interface, then programming it with something like Java/C/C++/... should be fine. You could go down more exotic routes to simplify the GUI programming; you could even setup a local web server, start a web browser and direct it at a local HTML/CSS page you crafted linking to addition server-side scripts (e.g. PHP or the like) starting the relevant apps. 

If you're not bothered about a graphical user interface, you could just start a BASH script in a terminal window, which presents a series of options and prompts for user input (e.g. enter the number corresponding to the app you wish to start).  

I'm sure there are rafts of other possibilities - it really depends on your requirements and your programming knowledge/ability. If you can give us more of a clue exactly what you're looking for (GUI/CLI, programming language, ... etc), I'm sure we can help you better :)

Any app you write can be started at login, and we can probably use some commands to GConf to disable the GNOME panels appearing on boot (or you can delete them), and it's a simple GConf command to disable the "desktop" (icons and right-click functionality). We can help you with all that if and when need be.

---

### Post by bitterbug on 2010-08-05
You could always remove the panels, so there's nothing for them to click on, and then use Avant Window Navigator to create launchers for only the items you need.

It's not a full splash screen but you can make the icons 100px and easy for them to see.

Even if it's not your final solution you can set up that temporarily in just a few minutes.

---

### Post by rakarnsunju on 2010-08-06
First off, thank you guys for the quick reply
 
I would like a GUI mode for them to use, but alas my use of program is limited at best.
 
Though I do like bitterbugs idea, any chance of a quick guide to doing it or pointing me to somewhere I can read up on doing it?
 
By the way just wanted to say thanks again, its been a few years since i have touched ubuntu and the last time i was on here and posted a question i was just hammered down by elites telling me I need to go learn the OS before I could post.
 
Its nice to see handing hands who dont think unbuntu is just for programs.
 
Thanks again
 
 
Ra

---

