---
title: "How can I make the menu bar transparent?"
date: 2012-08-17
forum: Desktop Environments
---

### Post by alreadytaken4536 on 2012-08-17
I've been looking at a few guides on how to change transparency in CCSM and I've been able to do a few things but nothing with the menu bar. No matter what I do, unless I change the window theme, the menu bar always looks like this:

[IMG]https://www.dropbox.com/s/o869vuntt79qvv8/Screenshot%20from%202012-08-17%2020%3A15%3A21.png[/IMG][IMG]https://dl-web.dropbox.com/get/Public/Screenshot%20from%202012-08-17%2020%3A15%3A21.png?w=603f6103[/IMG]

How do I change this ugly-*** grey bar? It looks okay in the High Contrast window theme:

[IMG]https://www.dropbox.com/s/mbamxi9r4vllok8/Screenshot%20from%202012-08-17%2020%3A18%3A12.png[/IMG][IMG]https://dl-web.dropbox.com/get/Public/Screenshot%20from%202012-08-17%2020%3A18%3A12.png?w=d282cddd[/IMG]

however, everything else in High Contrast pretty much looks horrible to my eyes. How can I edit the themes so that the menu bar is transparent in, for instance, Ambiance?

---

### Post by CrayMk7 on 2012-08-19
MyUnity is your friend.

[http://www.noobslab.com/2012/02/install-myunity-30-on-ubuntu.html](http://www.noobslab.com/2012/02/install-myunity-30-on-ubuntu.html)

---

### Post by Petro Dawg on 2012-08-19
(+1) MyUnity will work

Can also use "Advanced Settings" and change themes/icons by installing gnome tweak tool if you prefer.
[COLOR=red]
[/COLOR]```
sudo apt-get install gnome-tweak-tool
```I personally think the Grey looks good with the Ambiance theme and using Faenza-Ambiance Icons, but everyone's taste is different.

---

### Post by zombifier25 on 2012-08-20
> **Petro Dawg said:**
> (+1) MyUnity will work

Can also use "Advanced Settings" and change themes/icons by installing gnome tweak tool if you prefer.
[COLOR=red]
[/COLOR]```
sudo apt-get install gnome-tweak-tool
```I personally think the Grey looks good with the Ambiance theme and using Faenza-Ambiance Icons, but everyone's taste is different.

Last time I checked gnome-tweak-tool does not modify Unity's panel transparency. But MyUnity and CCSM does. In ccsm, go to Unity plugin > Experimental > Panel Opacity, and change the value to whatever you want.

---

