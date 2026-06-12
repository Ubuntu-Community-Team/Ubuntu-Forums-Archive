---
title: "set shermans-aquarium as screensaver"
date: 2009-06-14
forum: General Help
---

### Post by buzzmandt on 2009-06-14
i installed shermans-aquarium with sudo apt-get install shermans-aquarium.  It will run by using the command shermans.  when i go to system>preferences>screensaver it's not listed as a possible screensaver.  How do I put it into the screensaver list?

thanks

---

### Post by briguy47 on 2009-06-15
> **buzzmandt said:**
> i installed shermans-aquarium with sudo apt-get install shermans-aquarium.  It will run by using the command shermans.  when i go to system>preferences>screensaver it's not listed as a possible screensaver.  How do I put it into the screensaver list?

thanks

Here is how I got it working:

1. Open the .xscreensaver config file in a terminal:

```
gedit ~/.xscreensaver
```
2. Scroll down to where you see > programs: 
3. Then add the following just below it, just like the other entries:

```
shermans -root \n\
```4. Now run:

```
xscreensaver-demo
```5. Change the settings to your liking and hit preview.  


That should do it.  Let me know if you have any questions!  :D

---

### Post by hortstu on 2010-02-17
When I open the...

> gedit ~/.xscreensaver

it is blank.  any suggestions?

---

