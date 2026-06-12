---
title: "Some Xubuntu questions"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Peepsalot on 2006-06-03
Edit: I started off with a bunch of general question on how to configure Xfce better.  I've found the answers to some of these myself as I go. If someone can still help on the unanswered ones I would really appreciate it. 

1) How can I create a new Desktop Shortcut?
> you can create a shortcut with the shell command "ln" (thanks Morgengenuss)

2) How can I add this Desktop shortcut method from question #1 to my Desktop menu(right click)
> Answer: Items should be able to be added through Applications->Settings->Menu Editor.
But there is some bug that clears the menu entirely every time it is edited this way.
The file that is affected is "~/.config/xfce4/desktop/menu.xml".
The only solution for now is to edit this file manuallly(i use nano from a terminal).
I was a bit apprehensive but it is well documented and fairly simple.
Just remember to make a backup.

2a) Where can I see a list of icons and their names that are used in menu.xml?
> [COLOR="Red"]Partial Answer:[/COLOR] Icon files can be found in /usr/share/icons (I think the /usr/share/icons/tango/scalable icons are what xfce mostly uses)
But it is a lot of work to navigate around with all the redundant icons for different sizing, etc.  Is there some Application that makes it easy to see view a full list of icons at once, or something like that?


3) Is there a GUI file finder as part of xfce?
> no, but you can either use the shell command "find" or install the gnome desktop tools via synaptic pm (there's a filesearch gui included) (thanks morgengenuss)

4) Is there a program to define default programs for file extensions(eg default mp3 player)?  The "Preferred Applications" program is like a bad joke(only 3 things?!). 
> Answer: Default applications for file types can be set using Xfce's file manager Thunar.
Right click on a file of that type.
Select "Other Application..."  and make sure "Use as default for this kind of file" is checked.
It would still be nice to see a list of all at file associations at once, but I haven't found how that is done(or if can be done) yet.

5) How can I set keyboard shortcuts to open programs and is there a default shortcut for a file manager? (the preferred file manager in xfce is called thunar, right?)
> Answer: Applications Menu->Settings->Keyboard Settings (and click the Shortcuts tab)
Yeah I feel dumb for asking that one...

6) How do I configure screensaver in Xfce.  My computer locks up when this thing activates, and I have to hit the power switch. > go to settings > settings manager > screensaver and configure it.(thanks Morgengenuss)
The following screensavers were locking up my system instantly(even in preview mode):
Antspotlight
Flipscreen3d
GFlux(grab)
Pulsar(textures)
even the act of unchecking these would lock up my system, since it would automatically preview them when you do that.  I found that uncheking and quickly selecting another screensaver would let me change the setting without giving enough time for the preview to load and crash my computer.

By the way I think #2 is a good feature request to have this in the default xubuntu install.

---

### Post by Peepsalot on 2006-06-03
Nevermind about #5, i found it.#-o

---

### Post by Peepsalot on 2006-06-03
Is there some way to make a program window open in specific spot, or remember where it was placed last time?

---

### Post by i_m_meen on 2006-06-03
Use devilspie (it's in the repository). Or change the window manager from xfwm4 to Fluxbox or Sawfish. After that 
killall xfwm4 && fluxbox 
or
killall xfwm4 && sawfish
Then configure away (in Fluxbox you click on the titlebar and save the settings, in Sawfish you use the configure tool).

---

### Post by Peepsalot on 2006-06-03
Thank you I will try using devilspie.  I've installed it and am reading the documentation on it.  Haven't set up my .ds scripts yet but it looks like it will be able to do anything I want.

Does anyone have answers to my other questions in the first post?

---

### Post by Peepsalot on 2006-06-04
I've edited the first post with what I've learned so far, in case that helps anyone else with my problems.  Still could use some help with the remaining questions. :D

---

### Post by morgengenuss on 2006-06-10
ad 1) you can create a shortcut with the shell command "ln"
ad 3) no, but you can either use the shell command "find" or install the gnome desktop tools via synaptic pm (there's a filesearch gui included)
ad 6) go to settings > settings manager > screensaver and configure it. (or did i misunderstand your question?)

---

### Post by Peepsalot on 2006-06-10
Thanks a lot.

I found out about the ln command, but I was also wondering if there is some sort of gui interface for that.  I'm pretty sure there is something like this in gnome, you can right click and create launcher or something.  I just don't know what the binary filename for that is.
I'm not completely opposed to using the shell, but I kind of feel that most basic things should be accessible through the desktop like this.

And thank you for #6, that was driving me nuts.  For some reason I never clicked that setting manager before. I guess I kinda thought that was the title of the submenu, especially since every other icon is in alphabetical order but that one.
I think the way that menu is layed out is very confusing. Some of the settings are in both the settings manager, and in the menu, while others are only in one or the other.

---

### Post by fredvej on 2006-06-19
Suggestion for new questions :

5a) How can I configure a keyboard shortcut for display of the main menu, an equivalent to rightclicking on the desktop ?

5b) How can I configure a keyboard shortcut for display of the active window's menu, an equivalent to clicking on the window's menu handle ?

I hate having to use the mouse for activating and navigating in menus.  Fortunately XFCE allows the use of keys within the menus, but I can't find a way to open the menus without the mouse.

/Freddy

---

### Post by morgengenuss on 2006-06-19
ad 5b) actually I don't see the problem. when I press Alt+the underlined character in the menu (in firefox, thunderbird, thunar, etc.; actually in all the apps I quickly looked at after reading your post) I'm in the menu, just like in windoof.

and ad 5a) I remember having read a solution to this, but I couldn't find it straight away. Maybe take a look at the forum yourself. (Anyways, as soon as you've got the command for the menu you can just add the keyboard shortcut in Settings -> Keyboard Preferences -> Shortcuts  and then just add a new profile, cause you can't change settings in the default profile.)

---

### Post by fredvej on 2006-06-19
The menu I want in 5b) is the one where I can manipulate the window, e.g. maximise, minimise, move to other desktop etc.  It's not available with Alt-letter like the items in the menu belonging to the program inside the window.

I _did_ search the forum and the XFCE documentation for the magic command to bring up the main menu, but to no avail.  The only thing one can put as a command for a shortcut in the Settings -> Keyboard Preferences -> Shortcuts is an existing executable file - at least as far as I could find out.  I had hoped for a list of commands when I clicked the browse button, but no, only files can be chosen.  In /usr/bin there is no program named xfce-menu or something like that, so I can't choose that.

---

### Post by morgengenuss on 2006-06-19
i see, i see. sorry i got you wrong on 5b).
the answer is: settings -> window manager -> keyboard
there you should be able to adjust those shortcuts of yours.

and i searched a german forum for you to come up with this:
[https://wiki.ubuntu.com/Lkraider/XmodMap?highlight=%28xmodmap%29](https://wiki.ubuntu.com/Lkraider/XmodMap?highlight=%28xmodmap%29)
(of course this is the english equivalent of the german wiki page i found cause i assumed you don't speak german)

---

### Post by tbrminsanity on 2006-06-20
:confused:
I'm new to Xubuntu.  I have the following problem:
1. I have lost my application menu and need to know where I can replace menu.xml to get back the menu.  I need to know the format used in menu.xml and where to find the applications in the file structure.

---

### Post by fredvej on 2006-06-20
To morgengenuss :

In settings -> window manager -> keyboard there is a long list of commands for manipulating windows, but the "activate window menu" is not among them.  I'd hate to memorise a handful of shortcuts for manipulating windows when one shortcut to activate a menu would be enough.

The wiki-page on your link is about how to make X recognise and use a modifier key that is not already in the configuration.  That's not really what I'm asking for.  I know I want to use Ctrl-Escape to open the main menu and that this combination is usable for a shortcut, but I don't know which command to connect to that shortcut.  I have looked at the properties for the menu button in the panel's top left corner, but there is no command listed there, so I still have no idea which program XFCE runs to activate the menu.

Reading and understanding german is no problem for me, so if you find a useful text in german, please don't hesitate to post a link to it here.

What I want to do with these two shortcuts is to copy the MS Windows behaviour regarding main menu (aka the Start button) and the windows frame menu (activated with Alt-Spacebar).  MS Windows sucks at many things, but at least they got the shortcut access to important menus right.

---

### Post by fredvej on 2006-06-20
[QUOTE=tbrminsanity]:confused:
I'm new to Xubuntu.  I have the following problem:
1. I have lost my application menu and need to know where I can replace menu.xml to get back the menu.  I need to know the format used in menu.xml and where to find the applications in the file structure.[/QUOTE]

You might benefit from this thread : [http://www.ubuntuforums.org/showthread.php?t=184984](http://www.ubuntuforums.org/showthread.php?t=184984)

---

### Post by tbrminsanity on 2006-06-20
Thank you that fixed the problem.

---

### Post by morgengenuss on 2006-06-21
huhum... well, i fear now that i understand your problem i have to admit that i don't know. (i know you don't like it, but i would just memorize the shortcuts [which i actually do]. ;) )

---

### Post by Peepsalot on 2006-06-21
[quote=/usr/share/xfce4/doc/C/xfdesktop.html]
To open the menu run the command xfdesktop -menu, and for the windowlist use xfdesktop -windowlist.
[/quote]
Also, from the menu you can go to: Setting -> Desktop Settings.  Check to Allow xfce to manage desktop and then you can use right click to open a menu at any time(in the "Behavior" tab).  I think this was turned off by default for me(it will also let you see desktop icons if you want).  This is the only menu "shortcut" I use.

---

### Post by fredvej on 2006-06-22
[QUOTE=Peepsalot]To open the menu run the command xfdesktop -menu, and for the windowlist use xfdesktop -windowlist.[/QUOTE]

YES !  The command xfdesktop -menu is EXACTLY what I wanted for opening the main menu.  Now I have defined a shortcut to run that command, and it works beautifully    :D

The windowlist is not really useful to me in this context, I wanted the window menu for the active window to be opened with a shortcut.  Oh well, I guess I can memorise Alt-F5 to toggle maximise on and off, that is the window command I use the most.

Thanks a lot    =D>

---

### Post by Peepsalot on 2006-06-29
OK folks.  I've got another question now.  I have the option turned on for XFCE to manage my desktop icons.  Is there quick way to rearrange/sort these?  Or a setting to have them automatically stay in some arrangement?

The arrangement of these icons must be stored in a file somewhere, right?

---

### Post by afoglia on 2006-08-21
> 
1) How can I create a new Desktop Shortcut?


With Thunar, if you drag a file to a different folder or the desktop, while holding down the control and shift keys, you can make a link.  The pointer will change to two linked rings.

Likewise, copying can be done by just holding the control key, and the pointer will change from an arrow to a plus sign.

(I haven't tested this across disks yet.  Xfce might use the Windows-like default of copying across drives.)

---

