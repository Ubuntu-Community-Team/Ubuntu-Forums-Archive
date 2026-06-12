---
title: "Help Restoring my desktop envyroment"
date: 2010-07-23
forum: Desktop Environments
---

### Post by lgalford on 2010-07-23
Hi, 

I just installed an ubuntu desktop enviroment, after that I upgraded to the last version of ubuntu then I installed a kde enviroment. everything was working ok until try to clean the tool bar of some application and I run a script that should clean the icons enviroment but instead of that I delete all the icons and the tool bar of the top so now when I log in I just see an empty purple screen. 

is there a way to restore this configuration... please help me.. 

Regards
Luis Alford [-o<

---

### Post by vikas.sood on 2010-07-23
If you mean by pannels on the top and bottom you can try the solution here [http://ubuntuforums.org/showthread.php?t=392387](http://ubuntuforums.org/showthread.php?t=392387)

---

### Post by linux18 on 2010-07-23
-boot into recovery mode 
-drop to a root prompt 
-type "telinit 3 and login 
-type xinit
-in xinit type metacity & ; gnome-panel & ; nm-applet &
-don't close the terminal
-open a new terminal and type sudo apt-get purge kde-desktop && sudo apt-get install kde-desktop
this is a rather brute-force solution, but it works

---

### Post by WinRiddance on 2010-07-24
> **linux18 said:**
> -boot into recovery mode 
-drop to a root prompt 
-type "telinit 3 and login 
-type xinit
-in xinit type metacity & ; gnome-panel & ; nm-applet &
-don't close the terminal
-open a new terminal and type sudo apt-get purge kde-desktop && sudo apt-get install kde-desktop
this is a rather brute-force solution, but it works

The person who posted this thread had this is their very first post. Presumably this person knows little to nothing at all about terminal commands ... you might consider speaking down a little, err umh, ah, speaking more "human" that is .... ;)
I've been with Ubuntu about 15 months or so now but I don't think that I'd be very comfortable following those steps, especially without individual code blocks per entered line of code in the terminal. Just a thought .... ;)

---

### Post by PaulReaver on 2010-07-24
how do people feel about deleting the .gconf .kde and .config folders to reset all the settings?

is this a good or bad idea?

---

### Post by jerrykenny on 2010-07-25
A safe (if clumsy) method would be to create a new user, and then migrate your old data to the new users filesystem.

Hopefully leaving behind your old baggage .

---

