---
title: "LBZ3d Install on Ubuntu?"
date: 2010-12-11
forum: Gaming &amp; Leisure
---

### Post by speed86 on 2010-12-11
HI,


I Havent installed any game on Ubuntu before and i just downloaded IBZ3D from [http://www.lbz3d.com/](http://www.lbz3d.com/),

The problem is I have no idea how to install it, any ideas?

---

### Post by Mr. Hibba on 2010-12-11
First, double-click the file that you downloaded and it should bring up a program that shows you its contents.  There should also be an "extract" button somewhere; click on it and choose where you want to extract the folders to (Desktop or Home, for example).  Then, close the window if you wish and go to the newly extracted folder.  There should be a file named "lbzrun" in it, which when double-clicked should set up/start the game.  (May take a moment).  

If you run into any error messages, or the above doesn't work, just let us know and we'll see if we can help.  :)

Mr. Hibba.

---

### Post by speed86 on 2010-12-11
Thanks 4 the help I really appreciate it!

I have done what u said all is fine except when I run the game it opens up and closes after 5 secs........could it be compatibility problems  with hardware i have a Mobile Intel® GM45 Express Chipset GEM 20100330

In the debugreport.txt file it says FATAL ERROR, Debugger not enabled.


But the same game works great on Win7

---

### Post by Mr. Hibba on 2010-12-11
Hmm, not sure what's causing that.  You may want to send an email to the game's developers for more specific help.  

An alternative way to run it (not sure if it will help or not) would be by using the terminal.  The following example commands show basically how to do this.  

In this example, let's say the the lbz3d folder was extracted to your home folder.  

Open Accessories> Terminal (I think that's where it is; sorry if I'm mistaken).  Then, in the terminal, type "cd ~/lbz3d" without the quotes and then press enter. 

After that, type "./lbzrun" and press enter.  The game should start, but I can't gurantee it will run better (it should put some information in the Terminal after you hit enter, which might help find the problem).  

Note that the first Terminal command above is an example; if you extracted the lbz3d folder to your Desktop, then the command would be "cd ~/Desktop/lbz3d" .  

Hope this helps,  

Mr. Hibba.

---

### Post by Mr. Hibba on 2010-12-15
Also, you may want to check that you have the newest video drivers installed.  Click on the System menu, then Administration and there should be an option called "Hardware Drivers".  This should let you know if there are any updated stable drivers.  

Mr.  Hibba

---

