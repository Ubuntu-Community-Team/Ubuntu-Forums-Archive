---
title: "2 small Compiz Fusion problems"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by crimesaucer on 2007-07-02
Problem 1.) In my ccsm-->--General Settings-->--Focus And Raise Behavior...


I have my "Focus Prevention Windows" set to "none"... with: "Click To Focus", "Auto-Raise", and "Raise On Click", all checked...


... and in my ccsm-->--Place Windows-->--General....


I have "Place Windows" set as "Random" (have also tried "Centered", "Cascade", and "Smart")... 


Well, problem 1.) is that the mousepad in xubuntu (mousepad is a notepad app), always opens behind all my other open windows....it's the only xubuntu app that opens behind other apps????


It will only open on top of other apps, if I open mousepad with a Terminal command, or from my Xfce Menu, but if I click onto a file that's in a folder, and select that file with mousepad (like a gtkrc file that's inside of a gtk-2.0 directory), the mousepad gtkrc will always open behind all of the other windows that are open...so it's always buried beneath Firefox and my Thunar File System.




Problem 2.) Is about the grab screen....The "grab" screen is the dimming effect of of the computer screen that happens when you have to enter a password into the password dialog box for Administrative Tasks such as Synaptic, or Network Manager... it also happens when using "alt+f2" and typing commands such as: "gksudo thunar"... to open my Thunar with Root privileges. 


All of these "Administrative Task/Root apps" that require a password, open behind the "grab" screen.


I read somewhere that the dimmed "grab" screen is used for password security, and that it's recommended that you don't disable it (like mine is now)...


My "grab" screen always freezes on that dimmed screen, right after I enter my password, so then I always have to either do a manual shutdown, or a ctrl+alt+backspace...to start over again.


To temporarily fix it, I had to check the box to: "disable-grab", in my gconf-editor-->--app-->--gksu....


Now is there a better way to fix that problem? Other than disabling the "grab"?



Thanks for any help,
-c.

---

### Post by aidanr on 2007-07-02
Not gonna be much help to you, but just to say I also have the same behaviour with Mousepad.

---

### Post by crimesaucer on 2007-07-02
it's one small bug that I can learn to live with.

I'm more concerned about the password and the security issues with having the "grab" screen disabled.

---

### Post by firefeather on 2008-03-05
You might try enabling the "Window Rules" plugin and use [this wiki page]("http://wiki.compiz-fusion.org/WindowMatching") to help you put Mousepad either in the "above" section or put an exclamation mark before it and put it in the below section. So maybe like this:
```
Below: !title=Mousepad
```

---

