---
title: "Awn disappears!"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by Eyvind on 2008-01-02
Hi! I've just installed awn, and everything seemed to work, until I pressed the close button instead of the settingsbutton (when you rightclick on the fancy panel)...

To  run it again, I typed this in the terminal:
```
avant-window-navigator &
```
And it started, but when I close the navigator, the awn disappears too :(

How can I make it stay? reinstall? <-- How?

Here's a screenshot when it's gone:
[[img]http://bildr.no/thumb/137139.jpeg[/img]]("http://bildr.no/view/137139")

And now I've typed the command in the navigator:
[[img]http://bildr.no/thumb/137138.jpeg[/img]]("http://bildr.no/view/137138")

---

### Post by bharadwaj on 2008-01-02
uncheck the "maximized window don't cover the bar in the preferences window of awn . that would solve the window space issue.
And as far as sudden dissapearence of AWN thats a reported bug in it. AWN is still in its devoloping stage. hope they come up with a stable product very soon 
Eyvind: nice desktop! but can you tell me how did you create the transparent effect in side the window. I mea if we use compiz to do it even the title bar becomes transparent but in you screenshot that isn't the case
[[IMG]http://img146.imageshack.us/img146/9395/screenshotdd1.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshotdd1.png)

---

### Post by Eyvind on 2008-01-02
Nice desktop bharadwaj;)  You mean that trasparent window in the middle? It becomes transparent when you takes the screenshot :P 

To the case: "maximized window don't cover the bar" is unchecked, but I don't think that's the problem. 
I've tried to remove awn with synaptic package manager, but when I install it again, everything is as before I uninstalled.
When I run the command "avant-window-navigator", this pops up in the terminal:
> (awn-applet-activation:10459): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:10459): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed


Actually, I estimate to reinstall ubuntu and make a list over things that I need to install and get some order in things :P

---

### Post by jeyaganesh on 2008-01-03
Hi, I too have AWN disappearance problem. Whenever I am closing Terminal, AWN is disappearing. Moreover, everything I am doing with desktop is recording in the Terminal (Please see the attached screen shot). Do you have any solution for this?

For installing and uninstalling AWN, follow this forum,
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Thanks in advance,
Jay

---

### Post by jeyaganesh on 2008-01-03
Hi, I solved my problem of AWN disappearance followed by closing Terminal.
I simply put avant-window-navigator in start-up list, then restart the ubuntu to check. After restart, AWN appears automatically and not disappearing if I  close Terminal window. 

P.S. For making AWN on automatically on start-up follow this,

**System - Preferences - Sessions - Start Up Programs Ta**b

Then from there press 'New' and enter this:

Name: AWN
Command: avant-window-navigator

This will make AWN auto-start when you log into ubuntu. This way you don't have to waste time opening it every time you log on.

I saw this in  [http://ubuntuforums.org/showthread.php?t=602540](http://ubuntuforums.org/showthread.php?t=602540)

---

### Post by jeyaganesh on 2008-01-03
Hi, I found another reference for your problem. If program runs from terminal, it gives problem if we close the terminal. So run program through Alt+F2.

Reference forum;
(Please see the reply from user 'Forlong'
[http://ubuntuforums.org/showthread.php?t=649818&highlight=emerald+theme](http://ubuntuforums.org/showthread.php?t=649818&highlight=emerald+theme)

Have a nice time!
Jay

---

### Post by rainwalker on 2008-01-03
If you start a program from the terminal, it will close when you close the terminal.
Try starting AWN with Applications > Accessories > Avant Window Navigator

---

