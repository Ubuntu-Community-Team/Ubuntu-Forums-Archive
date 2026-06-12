---
title: "Compiz problem"
date: 2011-08-28
forum: Desktop Environments
---

### Post by aminfarhang on 2011-08-28
Hi all,
I'm new in ubuntu and when I wanted to change my Desktop with Compiz I don't know wath's happend (and I checked out wich options) that noyhing isn't in my Desktop and everything is disapear, even sidebar and turn on/off are disapear.
Does enyone could help me?
:(

---

### Post by Krytarik on 2011-08-28
Please see this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

It includes this guide, to enable the Cube, if that's what you tried to do:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by aminfarhang on 2011-08-29
Thank you Krytarik, it was solved.
for others that have same problem I listed your solution step by step below:

1.  right-click on desktop -> Create Launcher -> 
set Name to: Terminal
Command to:  gnome-terminal
Close  this window and then double-click the newly created launcher to get a  terminal.
2. If Unity and Compiz package is installed (if not follow upper links):
right-click on desktop -> Create Launcher ->
set Name to: Compiz
command to: /usr/bin/ccsm
3. double-click on new Launcher -> 
At the lower left of CCSM, click 'Preferences' and make sure 'Unity' is selected under 'Profile'.
4. Alt+Ctrl+F1
input your username and password
run: sudo service gdm restart

have fun,

---

