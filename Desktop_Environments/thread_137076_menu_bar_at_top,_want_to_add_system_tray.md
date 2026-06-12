---
title: "menu bar at top, want to add system tray"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Paranoid Randroid on 2006-02-27
Hello.

I'm using Kubuntu 5.10, with KDE 3.5.1, everything up to date as of this morning.  I've got the application menu bar at the top of the screen, as in OS X, and I'd like to add the system tray to it so that the menu stays on the left edge, and the tray (and clock) stay on the right.

However, when I tray to add the tray to the menu bar, the tray gets put somewhere in the middle of the bar and the menu itself goes to the right of the tray.

Is there any way to change this odd behavior?

thanks!

---

### Post by f1dave on 2006-02-27
Yes, I've heard a few things like this actually... I don't think there has actually been a solution forthcoming just yet, afaik its a bug. Perhaps you could search the forums though, there might be some updated news on it.

---

### Post by Jucato on 2006-02-27
you could always rearrange their positions, though.

---

### Post by gingermark on 2006-02-27
[QUOTE=Fenyx]you could always rearrange their positions, though.[/QUOTE]
Indeed. I've never thought of this as a bug. You add something to a panel, then move it to where you want it to be. If there is no option to move something by right-clicking then click the little black arrow that appears to the side of the relevant applet/button when you put your your mouse-pointer over it.

---

### Post by Paranoid Randroid on 2006-02-27
[QUOTE=gingermark]I've never thought of this as a bug. You add something to a panel, then move it to where you want it to be. If there is no option to move something by right-clicking then click the little black arrow that appears to the side of the relevant applet/button when you put your your mouse-pointer over it.[/QUOTE]

Hm.  My linux machine is at work, so I can't try it right now, but I don't remember either of those options being available to me.  Certainly the menu itself didn't have the normal ways to manipulate things on the main panel, black arrows or contextual menu entries.  

I'll try it again tomorrow.

---

### Post by aysiu on 2006-02-27
I think this is what you're looking for.

---

### Post by Paranoid Randroid on 2006-02-28
Thanks!  That does allow me to drag the tray to the right side of the screen.  The menu itself, though, is still stuck in the middle:

[IMG]http://locker.uky.edu/~jhcunn2/menu.jpg[/IMG]

There doesn't seem to be any way to move the menu itself, unless I'm missing some other obvious thing.

---

### Post by Jucato on 2006-02-28
I see what you mean. And I'm stumped as well... maybe when I wake up later, I might try to find out. keep you posted. :D

---

### Post by Jucato on 2006-02-28
Hi! just woke up a while ago and began experimenting on that menubar as promised. Try this and see what happens:
1. Add the menu bar
2. Add applets
3. Position the applets where you want them
4. Then, Alt+F2 (Run command) and type this in: dcop kicker default restart

Then see what happens.

---

### Post by Paranoid Randroid on 2006-03-02
Unfortunately, that did not work.  Thank you for your help, though!  I suppose for now I'll just deal.

(Now if I could just get xgl to work with an ATI rage 128 ...)

---

### Post by wisdoms on 2006-03-02
Hi, 
I could not find anything about the following problem. 
I've reinstalled Kubuntu 5.10 and some applications as Gaim, Acrobat reader or Skype, don't appear on the system tray!
How is it possible?
Cheers

---

### Post by Jucato on 2006-03-02
[QUOTE=wisdoms]Hi, 
I could not find anything about the following problem. 
I've reinstalled Kubuntu 5.10 and some applications as Gaim, Acrobat reader or Skype, don't appear on the system tray!
How is it possible?
Cheers[/QUOTE]
GAIM - try checking if the GAIM system tray plugin is installed and activated
Acrobat reader - I don't think it has a system tray icon
Skype - don't know about this
How are these related to this thread? :-k 

Paranoid Randroid: I'll get back to you in a while. I might have found a config file for you to tweak. :D

---

### Post by wisdoms on 2006-03-03
maybe I missed the place!
Anyway your advice about Gaim has been useful, 
thanx!

---

