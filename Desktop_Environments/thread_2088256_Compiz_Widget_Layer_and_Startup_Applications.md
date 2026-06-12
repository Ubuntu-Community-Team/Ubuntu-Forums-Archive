---
title: "Compiz Widget Layer and Startup Applications"
date: 2012-11-26
forum: Desktop Environments
---

### Post by iwishiwuzskiing on 2012-11-26
I like to have terminal set as a startup application so that it's available as soon as I boot and I like to store it on the Compiz Widget layer so it's always handy. In 10.10 this worked fine, but when I finally decided to drag myself out of the dark ages and made the switch from 10.10 to 12.10 I noticed strange behavior when I tried to set this up.

What I noticed was that when I have the rule set to put the terminal on the widget layer and have the terminal set as a startup application, after login the terminal window flashes onto the screen for a second then disappears and is nowhere to be found on any desktop or anywhere on the widget layer. However, the terminal icon has appeared in the Unity dock, and system monitor tells me that terminal is open.

After some experimentation I've observed the following: 
1) This isn't limited to terminal, it seems that any program that is pinned to the widget layer and a startup application does this
2) If I open a second instance of the program after logging in, the second instance shows up in the widget layer and behaves normally
3) If I turn off widget layer and reboot the startup applications open up normally

Any idea what might be causing thing?

---

