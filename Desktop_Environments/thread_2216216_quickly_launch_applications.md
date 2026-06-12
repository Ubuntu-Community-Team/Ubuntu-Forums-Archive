---
title: "quickly launch applications"
date: 2014-04-10
forum: Desktop Environments
---

### Post by viniosity on 2014-04-10
I've been away from Ubuntu for a few years and recently got myself an XPS-13 Developer Edition. I'm busy trying to get things set up the way I want. I'm close..

Right now the biggest issue is being able to quickly launch apps. In OSX I've got spotlight or quicksilver. I've found Indicator Synapse for Ubuntu which works really well but I can't seem to figure out how to launch it from the keyboard. The shortcut key I see assigned to it in the dconf-editor doesn't even work. Does anyone know how to activate indicator synapse from the keyboard? Else is there a recommendation for something that does this? I'm unsure if gnome-do or launchy are still maintained or recommended.

TIA

---

### Post by gifford on 2014-04-10
I'm not sure if this is the answer you are looking for but if you press the super key, it will open the launcher and display short cuts. Just hit the number of the app listed in the launcher and it will open.

---

### Post by deadflowr on 2014-04-10
If you're using Unity (the default desktop that Ubuntu now uses), then utilize the dash menu; which does basically what the gnome-do/synapse did/does.

Press the super key, or  click on the top icon in the left panel (it looks like the Ubuntu logo)
Then simply type the name of the app and hit enter.
Typically you will only need to type three characters for the app get listed.
Most of the time the app will be listed first within three characters, but not all the time.
(If that makes sense)

If you want to add it to the launcher, then simply drag it over, or launch the app and it will add it to the launcher, temporarily, which you can then add permanently by right clicking the launcher and selecting lock to launcher.

You can move apps on the launcher by simply pulling it out and putting it back in where you want it.

As stated, somewhat in post #2, pressing the super key and a number between 0-9 will open whatever apps are listed within those numbers. So the top ten apps can launch directly from the keyboard, with ease.
You can also launch apps beyond the top ten, with the keyboard, by press alt + F1, which will then allow you to navigate the apps listed all the way through. Simply press enter when you are on the app you want, to launch it.


All in all it is most likely to be easier to do, then I think I can explain.

As a quick tip, though, try opening the dash and type "privacy" and enter.
Then when a new window opens, look for a tab marked "Search" and click it.
Then toggle the on off button (there will only be one)
This should speed up the search function, otherwise it can get bogged down by the online searches.

I hope something in this helps.

---

### Post by viniosity on 2014-04-10
Hey, thank you both for your reply. I do see how can I use super + number to launch an app I'm looking for. Hitting super and then typing in something I don't access frequently seems to be a chore with the dash menu.

e.g. 

1. hit super
2. search for app and have it show up
3. use arrows to navigate to it
4. hit return

Am I missing something? 

indicator-synapse:
1. launch (need keybinding to work!)
2. type name of app
3. hit return

I do appreciate that dash is there but it's just not the app I'm looking for.

---

### Post by deadflowr on 2014-04-10
If you just type the name of the app it will show up.
It doesn't matter if you use the app once or everyday.

Also, if you press super + A it will open the app sub-menu directly.
Or right click on the ubuntu dash icon(top icon) and select applications.
Then click on the second section, called Installed, which will expand the listings.
apps in the dash-menu are listed alphabetically.

you can use filters to narrow the listings, if you want.
I never do, since my apps come up when I do a quick search by typing it's name.

Don't know if that makes any more sense then what I posted before...

As an added cavaet, the dash search will only find the apps that are located in the default locations.
(ie, /usr/share/applications, and /home/username/.local/share/applications)
So if you have an app somewhere else, it will probably come up as a file, instead of an app.

---

### Post by grumblebum2 on 2014-04-10
I find the dash slow and cumbersome to launch apps I don't have on the launcher.
I use kupfer for this purpose.
[ATTACH=CONFIG]251908[/ATTACH]

Don't know what indicator-synapse is but
there is also synapse which is similar to kupfer.
If your using Trusty you will need to get synapse from a ppa....
```
sudo add-apt-repository ppa:synapse-core/testing
sudo apt-get update
sudo apt-get install synapse
```
[ATTACH=CONFIG]251909[/ATTACH]

By default both of these use ctrl+space as the keyboard shortcut.

---

### Post by viniosity on 2014-04-10
@grumblebum2 Kupfer isn't as beautiful as indicator-synapse but it does what I need. Thank you!

---

