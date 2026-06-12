---
title: "A few questions regarding KDE"
date: 2006-05-10
forum: Desktop Environments
---

### Post by jyer on 2006-05-10
Hi, 
I've switch over to Kde since a couple of months. I've kind of got my habits now and hence are becoming lazy. I've therefore got a few specific questions concerning KDE for which I haven't managed to find an answer.
1. Is it possible to modifiy a .kde/startup script so that applications are automaticaly loaded into a specific desktop? I always boot Kde and then manually open firefox on Desktop 3, Thunderbird on n°4, Konqueror on n°5 and a terminal on n°6. Could these tasks be done automatically?
2. In the same field. I've created a link to the application Kmix in the folder .kde/startup so that the program automaticaly starts when Kde loads. Is it possible to send it directly to the system tray (it now pops up and I have to close it each time, a huge effort ;-)
3. Which files must I save to keep a copy of my kde configuration (layout, file associations, programs on startup, etc)?
4. Open a file from Konqueror in an other desktop. Exple: I've got Konqueror open on desktop 5, browse to a Open Office Document saved on my hard disk and what to open it on the Desktop 2, how shall I proceed without haven't to move it once it's open (you know, laziness ;-)?
Thanks in advance,
jr

---

### Post by cyracks on 2006-05-10
[QUOTE=jyer]
1. Is it possible to modifiy a .kde/startup script so that applications are automaticaly loaded into a specific desktop? I always boot Kde and then manually open [/QUOTE]

One way to do it is...
1.kde-control center->session manager->restore manually saved sessions
2.open all aplication which you wont to start at login and put them on right desktops.
3.right click on the top border of the window and select advanced->special windos settings->geometry->desktop (select force or remember)
4.in kde menu click save session

but as you pointed out it is also posible to add startup files to .kde/startup

---

### Post by jyer on 2006-05-10
Thanks for your answer.
Do you happen to know why Thunderbird doesn't appear when you save it in a session. All the other programs open fine, size and position respected (thanks for the desktop geometry tip), except for the desktop where thunderbird should be that simply stays blank...

---

### Post by jyer on 2006-05-12
I'm a bit puzzled that nobody can answer these straightforward questions...

---

### Post by aysiu on 2006-05-12
[QUOTE=jyer]I'm a bit puzzled that nobody can answer these straightforward questions...[/QUOTE] Because they're not straightforward questions, for the most part.

I've seen a lot of threads on these forums, and I don't think anyone's asked these questions before.

That said, I can answer at least this one: > 3. Which files must I save to keep a copy of my kde configuration (layout, file associations, programs on startup, etc)? Back up your .kde folder: ```
tar -cvvf .kde.tar ~/.kde
```

---

### Post by jyer on 2006-05-13
Thanks.
I mean, there must a way to control your destops individually. KDE seems to do it fine when restoring a session, hence it's bound to be possible to say: I wan't this to happen in this desktop. Should it be loading an application or opening a file...

---

### Post by vidak on 2006-05-13
> 
4. Open a file from Konqueror in an other desktop. Exple: I've got Konqueror open on desktop 5, browse to a Open Office Document saved on my hard disk and what to open it on the Desktop 2, how shall I proceed without haven't to move it once it's open (you know, laziness ;-)?
Thanks in advance,
jr

This is not a solution, but it's easier than right-click on the title bar, and selecting menus... In the last edition of kde, you can drag-and-drop the windows using the desktop manager (or whatever the name is...)

---

### Post by jyer on 2006-05-13
Ok, well lets put it an other way. 
If I wanted to write a servicemenus script so that I can select the Desktop via the actions option (when right clicking on the file), what should it contain?
I mean, how can I write that I want the file to open with its default application _in a specific desktop_?

---

### Post by kko1 on 2006-05-13
Agreed with aysiu. Your questions are not terribly straightforward. ;) 

I'll give it a try nonetheless.

> 1. Is it possible to modifiy a .kde/startup script so that applications are automaticaly loaded into a specific desktop? I always boot Kde and then manually open firefox on Desktop 3, Thunderbird on n°4, Konqueror on n°5 and a terminal on n°6. Could these tasks be done automatically?

I am not aware of a way to do it via the startup script. Possibly it exists, but it may depend on the individual programs. For KDE programs, something could probably be achieved by using dcop calls.

However, as you've found out, "kcontrol" -> "KDE Components" -> "Session Manager" let's you restore a manually saved session.

> 2. In the same field. I've created a link to the application Kmix in the folder .kde/startup so that the program automaticaly starts when Kde loads. Is it possible to send it directly to the system tray (it now pops up and I have to close it each time, a huge effort

My advice, if you haven't solved this yet: Remove the Kmix shortcut. Ensure that you have Kmix configured to dock to the panel. Set up a session with the programs you want to save, including Kmix minimized to the dock. Save the session.

At least for me, Kmix always starts minimized. (I use "Restore previous session" instead of "... saved session".)

> 3. Which files must I save to keep a copy of my kde configuration (layout, file associations, programs on startup, etc)?

Well, aysiu already answered this one. :) 

> Do you happen to know why Thunderbird doesn't appear when you save it in a session.

Can't tell you the exact reason, I can only confirm that it doesn't do it here either. It seems like a bug (or maybe a missing feature) somewhere in the interaction between KDE and Thunderbird, maybe on the T-bird side, but I haven't studied the details.

> 4. Open a file from Konqueror in an other desktop. Exple: I've got Konqueror open on desktop 5, browse to a Open Office Document saved on my hard disk and what to open it on the Desktop 2, how shall I proceed without haven't to move it once it's open?

As cyracks already hinted at, it is possible to set "Special Window Settings" in KDE. The downside of this is, that it is on a *per-program-basis*. That means that you can set Open Office to always open on Desktop 2, but you can't choose the desktop "on the fly".

For each application, you can right-click on the top bar, choose "Advanced" -> "Special Window Settings" -> "Geometry". What you could do is choose "Desktop" and _"Apply Initially"_, plus choose the desired desktop. (With this option you can change it afterwards, whereas with "Force" instead you can't change it, without removing the special setting.)

You can access all your special window settings by right-clicking a window's top bar, then "Configure Window Behaviour" -> "Window-Specific Settings".

> Thanks.
I mean, there must a way to control your destops individually. KDE seems to do it fine when restoring a session, hence it's bound to be possible to say: I wan't this to happen in this desktop. Should it be loading an application or opening a file...

Right. As said, it may be possible to do this also on a case-by-case-basis, utilizing the dcop calls, and someone may even have already done something like this - I am not aware of such, however.

For Konqueror, you could try this approach: "Creating Konqueror Service Menus"
[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html) . It may be possible to create a service menu that says: I want to open this file in OpenOffice, and I want it to open on Desktop 2.

"kdcop" can be used to study the dcop calls available - I found the call to change the Konqueror window title, or change window position / size, but didn't find a call to switch it to another desktop. Maybe you'll be luckier. :) 

Further documentation on DCOP here: [http://wiki.kde.org/tiki-index.php?page=DCOP](http://wiki.kde.org/tiki-index.php?page=DCOP) . The page shows links to a couple further guides, which I did not check.

Hope this helps, and if you decide to pursue the issue further, good luck! As always, please let us know if this has helped, and if / when / how you have managed to solve your problems.

kko

EDIT: You are apparently a mindreader, or were simply faster in going to this direction, as I hadn't posted this yet. ;) I hope this may still be of use in getting the service menu correctly set up.

Further EDIT: A google search on "konqueror service menu" might be helpful.

---

### Post by elamericano on 2006-05-14
You can install wmctrl for some command-line control of window placement. Unfortunately, it won't launch the apps into the other desktops. You have to open it an then move it. If you can give the window a unique title, that will help you identify and move it. It is a handy automation tool that you'll probably find a use for.

---

### Post by kaveraj on 2006-05-16
I use kde 3.4.3 and I found out that the autorun scripts reside in ~/.kde/Autostart

Donno if this helps but there is an app called alltray which>  docks any application with no native tray icon (like Evolution, Thunderbird, Terminals) into the system tray. A high-light feature is that a click on the "close" button will minimize back to system tray. It works well with Gnome, KDE, XFCE 4*, Fluxbox* and WindowMaker*. Detailed instructions on how to install is [here]("http://ubuntuforums.org/showthread.php?p=1023217#post1023217").

I came across an app called Devil's pie that claims to do what the user wants [from here]("http://ubuntuforums.org/showthread.php?t=75749t"). But it seems to be a gnome app. Not sure ..

---

### Post by ComplexNumber on 2006-05-16
> But it seems to be a gnome app. Not sure ..
yep, its a gnome app.

---

### Post by Jomdom on 2006-05-23
Regarding your second question, it is possible to launch a program and minimize it directly to the tray by:

1) Opening the properties for the shortcut.
2) Selecting the Application tab.
3) Clicking 'Advanced Options' near the bottom of the window.
4) Checking 'Place in system tray' in the following window.
4b) I've found that when launching a program directly to the system tray, the launch feedback cursor hangs, so I also uncheck 'Enable launch feedback' in the same window.

Ta-da! Should work just peachy. As the others have mentioned, just throw this shortcut in your *Autostart* folder in *$HOME/.kde/*

---

### Post by pwaldo on 2006-05-24
[QUOTE=jyer]Thanks for your answer.
Do you happen to know why Thunderbird doesn't appear when you save it in a session. All the other programs open fine, size and position respected (thanks for the desktop geometry tip), except for the desktop where thunderbird should be that simply stays blank...[/QUOTE]

This is because Thunderbird is not a KDE application.  KDE is able to run non-KDE applications fine, but certain advanced features are unavailable.

---

### Post by charles.figura on 2006-05-26
Stumbled across this, didn't see that anyone had mentioned kstart yet.  I do the same kind of thing, and use the .kde/Autostart directory to cue everything up.  Take a look at kstart - there's no man page, so do a 
kstart --help

You can specify desktop and behavior.  For example, I like Thunderbird on desktop 6 - so in .kde/Autostart, there's a file I named thunderStart, which looks like this:
```

#!/bin/bash
kstart --desktop 6 --windowclass "Mozilla-thunderbird-bin" --maximize /usr/bin/mozilla-thunderbird

```

It's important to specify either windowclass or window title, otherwise behavior will be somewhat chaotic.  To find out, get thunderbird (or whatever you'd like to start up), type:
xprop | grep WM_CLASS
and click the little x-cursor that shows up on the window you're interested in.  You'll get two strings, one capitalized, one not.  Use the Capitalized one.  (Kapitalized, maybe, for Kubuntu?)

The help will show you all of the different flags you can use.  Currently, I have Firefox start up on one desktop, thunderbird on another, and a nixieclock that shows up on all desktops.  Even better, kstart allows me to configure it such that my clock doesn't show up on the taskbar or pager (who needs that cluttering things up?)
```

#!/bin/bash
kstart --alldesktops --skiptaskbar --skippager --window "nixie time"  /home/figura/bin/nixieqt.py

```

This seems to work really well.  Oh - since firefox *will* start up for a saved session, you may want to leave it out of the Autostart OR turn off the session saving.  Otherwise it will try to start up two firefoxes (firefoxen?  firefoxii?).

Hope this helps -

---

### Post by kko1 on 2006-05-27
Hi!

[QUOTE=charles.figura]didn't see that anyone had mentioned kstart yet.[/QUOTE]

Thanks, that's a nice one to know. :D 

kko

---

