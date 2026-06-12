---
title: "linux system optimizer"
date: 2009-04-08
forum: General Help
---

### Post by ninos_loves_u@hotmail.com on 2009-04-08
i was wondering if theres a program to optimize ubuntu like fix errors, remove history, speed up the system, remove unneeded packages, maybe defrag the harddrive for faster access

---

### Post by kerry_s on 2009-04-08
> **ninos_loves_u@hotmail.com said:**
> i was wondering if theres a program to optimize ubuntu like fix errors, remove history, speed up the system, remove unneeded packages, maybe defrag the harddrive for faster access

it's not windows.

---

### Post by HermanAB on 2009-04-08
No, because none of that will actually do anything useful.

Linux is a modular system with a decent scheduler and memory manager.  It doesn't need Windows housekeeping.

---

### Post by mdgrech on 2009-04-08
I noticed your new...just wanted to mention that Ubuntu is already optimized so to speak.  Changed setting does not change the default ubuntu install.  Like already said its very modular.  Think of it like your PC, it takes a lot of different parts and they all work together.  If you hard drive fails you just get a new hard drive.  Ubuntu is same the way, each bit of ubuntu is kind of chill laxing in its own little world.

---

### Post by dcstar on 2009-04-08
> **ninos_loves_u@hotmail.com said:**
> i was wondering if theres a program to optimize ubuntu like fix errors, remove history, speed up the system, remove unneeded packages, maybe defrag the harddrive for faster access

The new version of Ubuntu (9.10, soon to be released) will have a tool for doing some of these things, but most on your list are unnecessary and can actually damage your system if done without a thorough understanding of what you are actually doing.

The bottom-line is you no longer need to worry about such things using Linux.

---

### Post by ivanvajar on 2009-04-08
Linux doesn't need such maintainance. Are you having some problems or you just needed an info on this?

---

### Post by binbash on 2009-04-08
BleachBit

---

### Post by Lunx on 2009-04-08
> **dcstar said:**
> The new version of Ubuntu (9.10, soon to be released) will have a tool for doing some of these things, but most on your list are unnecessary and can actually damage your system if done without a thorough understanding of what you are actually doing.

The bottom-line is you no longer need to worry about such things using Linux.

Yeah, Jaunty has a new app in the menu, Computer Janitor. Not sure what benefits it has that you can't do through the terminal with ```
sudo apt-get autoclean
```The above is used to clear the cache of downloaded packages) 

This next command removes packages that are no longer required after you have unistalled software ```
sudo apt-get autoremove
```

---

### Post by duckfeet on 2009-04-16
I like Bleachbit myself: reminds me of ccleaner, and it sure found plenty to remove on my dell-mini, I need the space, and I just like seeing things disappear, anyway...

---

