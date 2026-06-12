---
title: "Uninstalled Nautiulus and ubutnu One cant access desktop or apps"
date: 2011-09-12
forum: Desktop Environments
---

### Post by GumpTron on 2011-09-12
Okay I know I screwed up again so here it goes get ready :popcorn:


I had read about themes and different interesting icons I could use so I installed some repository and installed what I believe were some Nautilus theme related things. Long story short I wasn't able to get the themes to work so I wanted to uninstall it and I also wanted to remove the drop box cloud thingy from the top bar. I believe that's where I went wrong and uninstalled too many things.

Currently, I boot into Ubuntu and there is a x mark for my mouse pointer, a black desktop with no side bar. I can see the top bar and its like the older style was and I can click the old style Firefox icon but it wont open the browser and i get an error. I'm pretty sure its opening but there is a problem with the desktop effects or something to that effect. Can someone help a noob out?


p.s. worse come to worse I am totally fine starting from scratch with ubuntu, if I have to do that is there an easier way than popping the install cd and doing it that way? Thank you! :p

---

### Post by GumpTron on 2011-09-12
Here are some updates with error messages I can get:


Eauthority file home/oneof2/.ICEauthority

problem configuration server

something like this : usr/lib/1:bgconf/gconf-sanity-check-2 exited with status 256

after clicking okay through both errors, whats left of the desktop said something like "could not load config"

hope this helps

---

### Post by coffeecat on 2011-09-12
> **GumpTron said:**
> I believe that's where I went wrong and uninstalled too many things.

I think you did! :wink:

Nautilus is not just the file browser - it's the desktop too, so if you have uninstalled it, you've taken away a goodly chunk of you GUI.

Here is a suggestion. It needs an internet connection. If network manager is still working but invisible then you should be OK. If the stuff that's been uninstalled has affected network manager's functionality, then this will likely fail.

Boot up and login to your broken desktop. Now press alt-ctrl-F1 which will take you to a virtual console - all text. Log in. Now:

```
sudo apt-get update
```

If you get output and no errors, all well and good. If you get connection errors, this is not going to work. If you have a connection, now:

```
sudo apt-get --reinstall install ubuntu-desktop
```

The package ubuntu-desktop is a so-called metapackage which has as dependencies everything needed for the Ubuntu desktop GUI, so hopefully that will reinstall everything you've lost.

Failing that, I think you might have to do a fresh install of Ubuntu. And answering your question. The easiest way of reinstalling Ubuntu is by using the live CD (or live USB). :)

---

### Post by GumpTron on 2011-09-17
was not able to achieve success so I just reinstalled the whole darn thing. Thank you for your help :p

---

