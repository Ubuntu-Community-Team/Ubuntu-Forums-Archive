---
title: "cool trasnparent terminals"
date: 2005-03-29
forum: Desktop Environments
---

### Post by somuchfortheafter on 2005-03-29
how do i create a transparent terminal with no borders like the ones in this screenshot?
[http://www.gentoo.org/images/shots/godoisw.jpg](http://www.gentoo.org/images/shots/godoisw.jpg)
also im thinking it is aterm but the best i can get is shown is in my screenshot in my sig, obviously not the same thing lol.

---

### Post by TravisNewman on 2005-03-29
Got this for you:
[http://64.233.161.104/linux?q=cache:xXw_ZRpnwScJ:linux.derkeiler.com/Mailing-Lists/Fedora/2004-03/4101.html+transparent+borderless+terminal&hl=en](http://64.233.161.104/linux?q=cache:xXw_ZRpnwScJ:linux.derkeiler.com/Mailing-Lists/Fedora/2004-03/4101.html+transparent+borderless+terminal&hl=en)
It's the google cache with highlighting.

There are two solutions, one with Eterm, and one with gnome-terminal

---

### Post by yusufk on 2005-03-30
I managed to follow most of the instructions for gnome-terminal, however I cant do step 5 because I dont see the options mentioned in Gnome Menu --> Preferences --> Windows ?

5) Shut off the borders and other window configuration. Here's some of

that advanced window manager functionality that Metacity lacks.



Start your Gnome-terminal.

Bring up the configuration manager for sawfish:

 

Gnome Menu --> Preferences --> Windows



Go to the Matched Windows tab and add a Matcher. Select matcher by

Name (in the left drop down) and hit the grab button.

Click on your gnome-terminal. You should now have a matcher by Name

called ^bkgrnd$ or whatever your window title is.



Here's how I configured the "actions" tabs:



Placement tab: Depth = -1 This keeps the background shell in the

background not allowing it to come forward above other windows.

   

Focus tab: Raise on focus = no, nothing else checked

Appearance tab: Frame type = none. This gets rid of the border.

State tab: Ignored=yes, Sticky=yes (puts the terminal in all

workspaces), Window list skip=yes

Other tab: Nothing checked

---

### Post by somuchfortheafter on 2005-03-30
thanks for that and i also found that this command works as well
 Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=65x25+30+30

---

### Post by Shaggy on 2005-04-07
I hate to bring up an old topic but if someone could toss up a how-to on how to do this I would appreciate it muchly, I've been trying to figure out how to get this going with gnome terminal, instead of eterm.

---

### Post by Nis on 2005-04-07
[QUOTE=Shaggy]I hate to bring up an old topic but if someone could toss up a how-to on how to do this I would appreciate it muchly, I've been trying to figure out how to get this going with gnome terminal, instead of eterm.[/QUOTE]
 To do so would involve turning off window decorations for the terminal window which is something Metacity (the window manager) cannot do according to some googling.  Sorry. :(

---

### Post by Shaggy on 2005-04-08
Hmmm but a few posts up panicked thumb said there was a way to do it with gnome terminal.

 :-s

Guess I'll search some more, I'll post up if I find anything.

---

### Post by Nis on 2005-04-08
[QUOTE=Shaggy]Hmmm but a few posts up panicked thumb said there was a way to do it with gnome terminal.

 :-s

Guess I'll search some more, I'll post up if I find anything.[/QUOTE]
 In the next post yusufk mentioned that he did not see options that were specified in the howto thumb pointed out.  Unfortunately I really do think that Metacity does not currently support removing window decorations.

---

### Post by Leif on 2005-04-08
[QUOTE=somuchfortheafter]thanks for that and i also found that this command works as well
 Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=65x25+30+30[/QUOTE]

This works a bit weirdly for me: the geometry option doesn't really work. I can't change the size or the starting position. Also, the starting position changes depending on whether another app is maximized; if so, it's on the left edge, if not, it's a bit further right. How do you make sense of this ?

---

### Post by bonifacio on 2005-04-08
If you want transparent gnome-terminal see [this](http://ubuntuforums.org/gallery/showimage.php?goto=lastpost&i=&p=9)

---

### Post by Cimmerian on 2005-04-08
Just thought I'd mention that since certain apps don't have a window border, metacity supports it, just not as an option. I guess it makes a little sense as someone could accidently enable this and have trouble changing it back, and it adds "clutter" to prefs or some completely different explanation. This is probably part of the hints that most modern window managers support, a setting for borderless, that is. 

So you could as well say that it is gnome-terminal that doesn't have the option of removing the border, as metacity would do it if the terminal "asked"...

I know, this didn't help at all...

---

### Post by Leif on 2005-04-08
[QUOTE=bonifacio]If you want transparent gnome-terminal see [this](http://ubuntuforums.org/gallery/showimage.php?goto=lastpost&i=&p=9)[/QUOTE]

But that's not it, that's just a transparent background. The aim is transparency + no borders, for that cool "the desktop is my terminal" effect.

As a side note, there's an easier way of getting a transparent background than the one in that link : in a terminal, edit->current profile->effects->transparent background. You also get to set its level this way.

---

### Post by telmo on 2005-04-08
Yep! That's basic! :)

---

### Post by RastaMahata on 2005-04-08
It would be soooo good to have that kind of terminal in gnome in an easy way... maybe with gdesklets or something? :s

---

### Post by doclivingston on 2005-04-09
You should be able to get a border-less windows if you do the following (at least on my machine) and don't have more than one tab open.

a) put it into fullscreen mode (in the menu, or via metacity)
b) make a profile with the scrollbar set to none (in the scrolling tab)
c) turn off the menubar (in the menu)

---

### Post by andrewsawyer on 2005-06-12
Hi all,

I have used the command

Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=65x45+150+50

to put the Eterm window on my desktop, just the the right of my desktop icons, so they are still visable, and it lookd great.

However, I have an Eterm 0.9.2 'button' on my menu bar.  I think thats what it's called.  The bit that lets you quickly switch between apps.  Is there a way to remove this?  I've tried using Alltray, however the 'button' is still there when the app is loaded on the desktop.  For some reason this also puts the transparency of my desktop out of alignment through Eterm???

If it's possible, could someone please post how to do it?

Many thanks,

Andrew

Oh, also, is it possible to set on load that it is visible on all screens rather than just the one it originally loads on?

---

### Post by Digitallysick on 2005-06-12
I got eterm going, transparent, but still have it at the bottom of my task bar, recently i started useing it with KDE, it looks great. Its to bad they cant make it 100% transparent like the osx term, where i could have term up and read this message underneath instead of just showing the desktop back ground

---

