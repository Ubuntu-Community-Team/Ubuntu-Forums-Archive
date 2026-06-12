---
title: "Anyone have Microsoft Wireless Desktop 1.0A mapped well?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Joey French on 2006-06-11
Hi all,
Making a serious go at (re)setting up all of my Micro$oft Wireless Desktop buttons and such, and just wondering if anyone had an easy solution. I have done hotkeys, xbindkeys, keytouch, etc... and had a good configuration, but after changing default apps, DE, and moving to Dapper, I seemed to have lost functionality. Anyway, somebody tell me a quick way to set these guys up again, cause mapping everything again is a headache, don't really wanna do it again. I use Kubuntu 6.06, and have adjusted "Keyboard Layout" under KDE 3.5.3, but no joy. At this time, F1-F12 do nothing, nor do my "Web"," Home", "Mail", "Messenger", "My Documents" or 5 "My Favorites" multimedia keys. Also of note, when checking using xev, a number of these keys do not register an action. Volume keys do function correctly, but FF, Rew, Stop, Play I would like to map to amaroK (or Xine) and "Calculator", "Log Off" and "Sleep" I would like to add functionality to as well. 

This is important to me as the girlfriend uses the computer at home, and the functionality of these keys will up the GFA (Girl Friend Approval) Rating tremendously. After this gets sorted, I hope to get all of the buttons on my wireless mouse working as well. Maybe someone has an easy solution?

Thanks all,
Joey French

---

### Post by Joey French on 2006-06-11
Hmmm, guess not..? Okay, any keyboard then. Simplest way to set up multimedia keys?

---

### Post by matthew on 2006-06-11
[quote=Joey French]Hmmm, guess not..? Okay, any keyboard then. Simplest way to set up multimedia keys?[/quote]It's a weekend...I bet someone will reply in a day or two with some great ideas.

In the meanwhile, take a look at this thread and see if it helps you.
[http://ubuntuforums.org/showthread.php?t=193936](http://ubuntuforums.org/showthread.php?t=193936)

---

### Post by lonegeek on 2006-06-11
Hmm in ubuntu with gnome... most of them i was able to map...well all of them except my favorite keys....

Press f lock? maybe thats why f1-f12 dont work...

---

### Post by Joey French on 2006-06-11
Woohoo! One set of keys down, now just to set about getting all the rest going. So, when I get them all mapped, is there any way I can save the configuration so I can move it to my upgrades as long as I have this desktop? Resetting up the keyboard and mouse every time is for the birds. Last time it took forever to get all the buttons on my mouse taken care of.

---

### Post by Joey French on 2006-06-16
Okay, so I guess noone has full multimedia keys setup on this keyboard. So, I am gonna set them all up, and post the config here, for those who have the same problem in the future.

---

### Post by naitsirhc on 2006-06-19
Hi Joey,

I found a site that shows how to setup the multimedia keys in KDE.

[http://www.linuxquestions.org/hcl/showproduct.php/product/1499/sort/1/cat/443/page/1](http://www.linuxquestions.org/hcl/showproduct.php/product/1499/sort/1/cat/443/page/1)

Under the Regional and Accessability settings you can set up a keyboard layout and choose the Microsoft keyboard from the drop down list.  the multimedia keys will be recognized by KDE.  Is working great for me in amaroK

Hope this helps! :)

---

### Post by Ubuntiac on 2007-05-31
The KDE System Settings -> Regional Settings -> Keyboard thing didn't work at all for me. Didn't seem to do anything.

Touchkeys however worked absolutely perfectly. 

Just installed it from the repos, "touchkeys" from terminal, selected Microsoft Multimedia 1.0 from the dropdown and presto! All function keys and media keys are perfect. No fiddling with mapping and assigning keys needed. Only wierd thing is that they've reassigned F10 "Spell" to open up their own program (touchkeys). No biggie as who needs a key assigned to "Spell", but slightly odd.

Touchkeys has my vote for "Most needed package to be included as standard in next *Ubuntu release."

For the record I'm on Kubuntu Feisty
Touchkeys 2.2
CAVEAT: I do have the *WIRED* M$ Multimedia 1.0A

---

