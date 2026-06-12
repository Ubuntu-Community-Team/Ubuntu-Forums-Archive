---
title: "Fire Effect"
date: 2008-03-25
forum: Desktop Environments
---

### Post by banzeuk on 2008-03-25
hey there guys, i was just wondering if you could help to add those effect when you close a window such as fire and etc. do i need to have Beryl installed? :s im kinda lost please help me! 

Thanks!

---

### Post by scragar on 2008-03-25
compiz is all that is needed, and it comes pre installed to gutsy.

you may want to install the options:
```
sudo apt-get install compiz-settings-manager
```
firstly check you have desktop effects turned on:
system > preferences > appearance 
then the visual effects tab, set it to either full or custom(in which case click customize and turn the draw fire effect on).

---

### Post by Tews on 2008-03-26
Be sure to set the visual effects to random and all will.be well! :)

---

### Post by Junkieman on 2008-03-26
hey banzeuk, yeah scragar has it pretty much covered (you could also use Administration -> synaptic package manager to search for and install beryl settings manager).

just note that it does make your system a little more unstable, especially if enabling desktop effects prompts you to select a proprietary graphics driver (like nVidia or ATI).

just remember these two importand things i have discovered thus far:

1) if at any time everything seems to hang, press Ctrl + Alt + BACKSPACE. This will reset Gnome (or KDE).

2) if you managed to get back in and your windows are all broken (ie no window borders), you can reset the default window manager by pressing Alt+F2 (or getting into a console) and executing this command: 

```
metacity --replace
```

And have fun playing around with the settings!

---

### Post by banzeuk on 2008-03-26
i cant get "draw fire effect" option! any idea why?

Thanks a lot!

---

### Post by scragar on 2008-03-26
it's called "paint fire on screen" and comes under the effects section. I couldn't remember what it was called earlier, sorry.

---

### Post by banzeuk on 2008-03-26
ive selected that before,, and nothing changes. the window just fades away :S 
**** am a real noob! lol

---

### Post by scragar on 2008-03-26
<shift>+<super>+<click> = start drawing fire
<shift>+<super>+c = clear fire

super is the key that normaly has the windows logo on it, if you wish you can change these default key bindings using the Actions tab

---

### Post by banzeuk on 2008-03-26
I LOVE YOU MAN!  thanks a lot !

---

### Post by Arwen on 2008-04-20
I don't think it's necessary to start a new thread so I'll post in here.
I have ubuntu 7.04 and have installed compiz and extras by synaptic
I typed>  sudo apt-get install compiz-settings-manager and it couldn't find that package.What can I do about it?

Thanx in advance

---

### Post by scragar on 2008-04-20
I know compiz is installed by default on gutsy(7.10), but I don't think it installed so easily on feisty(7.04).

a quick search on [http://packages.ubuntu.com](http://packages.ubuntu.com) reveals gnome-compiz-manager which sounds to be the correct package, compiz is a dependency as well, so that should install rather easily.
```
sudo apt-get install gnome-compiz-manager
```

---

