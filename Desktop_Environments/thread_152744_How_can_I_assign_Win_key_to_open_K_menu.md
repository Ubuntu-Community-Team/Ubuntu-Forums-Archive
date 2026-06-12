---
title: "How can I assign Win key to open K menu?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by snowboard975 on 2006-03-30
I used Win key to open start menu in windows. But Win key does not work in linux to open K menu. Is there another keyboard shortcut to open K menu? How can I assign the key to open the K menu??

---

### Post by arnieboy on 2006-03-30
linux developers feel that no key should be assigned without any combination to a job because if its done, then that key becomes useless for any other job (cannot be used in combination with anything else). In  Breezy Gnome, you can still use the win key to pop up the gnome menu because its not used in combination with anything else. however, in Dapper, this has been removed and you can no longer use the win key as a standalone shortcut.
KDE already disallows use of standalone shortcuts of keys.

---

### Post by John.Michael.Kane on 2006-03-30
This may help you [http://www.ubuntuforums.org/showthread.php?t=79560&highlight=windows+key](http://www.ubuntuforums.org/showthread.php?t=79560&highlight=windows+key)

---

### Post by snowboard975 on 2006-03-30
Great! It recognize Win key alone! But I dont' know what to input in the "Action" blank in the bindkeys-config window. I mean, I don't know what is the command for K menu. I tried inputting "kmenu" only to fail. What should I input there to get the same effect with clicking the K menu icon in the taskbar?

[QUOTE=SD-Plissken]This may help you [http://www.ubuntuforums.org/showthread.php?t=79560&highlight=windows+key](http://www.ubuntuforums.org/showthread.php?t=79560&highlight=windows+key)[/QUOTE]

---

### Post by binarysleeper on 2006-03-31
Spotted this thread and though I should figure this out as it has been bugging me for a while. The windows key is very useful to me and I've yearned to get it functioning. 
Anyhoo, after perusing these threads and installing xbindkeys etc. I ran into the same problem: what command do you issue to open the menu?
I came across an article in a Kubuntu thread the other day that got me thinking and led me to find the answer ([http://www.terra.es/personal/diegocg/kde/]("http://www.terra.es/personal/diegocg/kde/")): DCOP!

DCOP is a bit like a desktop control by command line type thing [my descriptive powers are failing me at the mo'] and you can make DCOP compliant apps do things (check out the above links' section on DCOP, it's pretty cool). 
 Apologies for my rambling answer but here is the bit you need:
In the command box enter:
```
dcop kicker kicker popupKMenu 1,695
``` This took a bit of trial and error to get the positioning right, but the coordinates specify 1 pixel from the left of the screen and 695 pixels from the top **to the top of the menu** i.e. this works for my desktop resolution and curently configured menu. Just play to get it where you like. If you want it to pop up under the mouse cursor use 0,0. 
Press the "Run Action" to test it.
**Edit/**
Vodka has dulled my senses somewhat and I've just noticed that you can substitute "popupKMenu" with "showKMenu" and not have to faff about with the silly coordinates malarkey. Hohum
**/Edit**

For those who are interested how I found the right  dcop directive, I used the DCOP browser called "kdcop" and messed about with the objects shown there. Googling a particular object would probably be helpful to find specific usage.

If anyone else finds any useful dcop actions for keybinding please let me know.

Cheers all,

---

