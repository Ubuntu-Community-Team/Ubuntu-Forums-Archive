---
title: "hot corners"
date: 2009-06-18
forum: Desktop Environments
---

### Post by mblack3 on 2009-06-18
Hello

i recently downloaded/installed brightside which allows me to activate hot cornerns on my desktop, aka, hover over a certain corner to perform a specific action. I got it to work with screensaver and show desktop but not to tile all the windows. I want to hover over the top-right corner and immediately show all the windows i have open, similar to the scale function found in ccsm. i am aware that in ccsm, you can set mouse bindings and hot corners but i cant get around have to hover and click in the corner to activate scale. How do i do that. Or... brightside has a custom action option---is it possible to set that custom action to perform scale from ccsm?---running ubuntu

Thanks for any help i may recieve.

---

### Post by john.nicholls on 2009-06-18
I don't know any way to achieve this, but you might get a response on the Compiz Community Forums [http://forum.fusion-compiz.org/](http://forum.fusion-compiz.org/)

---

### Post by celticbhoy on 2009-06-18
This feature is available in ccsm in scale plugin

---

### Post by mblack3 on 2009-06-18
yes i know about scale in ccsm but i cannot set it to work by just hovering to the corner, i have to click the corner which i dont want to have to do
thanks

---

### Post by mblack3 on 2009-06-20
what about this as a possibility, could anybody do this
this was a suggestion i found online

What you will want to do is mess with your compiz settings to get the function you want performed to occur via keystroke or something (there might even be 'hot corners'-like ability in compiz already), then you will have to write a script or figure out how to trigger this function from the commandline (dbus, echo commands, whatever). Finally, you setup brightside to have a corner trigger a "Custom Action" (You set this in the brightside properties window.), and run the command or script that you have created (and undo that too if needed).

---

### Post by zhocchao on 2009-06-21
I don't use compiz. But couldn't you assign a key shortcut to your tile (or scale or whatever) option? Brightside could send this key with xte.

---

### Post by mblack3 on 2009-06-21
ok i am sorry
i tend to need to be walked through things :)
now yes i have scale right now as shift, alt, up i believe

---

### Post by Ck.asdf on 2010-07-17
Hello, for those who cannot find "Brightside" after installing it, I found out a solution:

> 
Now, it used to be that a menu item would appear in System-->Preferences called "Screen Actions", and this would allow you to modify which corners do what. For some reason, this may not appear in Karmic. You can create a new menu item by going to System-->Preferences-->Main Menu and making a new item in the System-->Preferences menu called "Screen Actions" with the program setting as:

[quote]
brightside-properties


From there, you can adjust things to how you want them.
[/quote]

This was taken from:
[http://www.supportforums.net/showthread.php?tid=2831](http://www.supportforums.net/showthread.php?tid=2831)
Which has many other interesting things to install. :)


Alternatively, you can run "brightside-properties" from the "run" dialog (alt+f2) or from the terminal.

---

