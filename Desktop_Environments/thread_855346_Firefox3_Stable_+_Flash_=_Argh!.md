---
title: "Firefox3 Stable + Flash = Argh!"
date: 2008-07-10
forum: Desktop Environments
---

### Post by chrispottrell on 2008-07-10
Hi guys,

I know it's the same old same old with Flash, as Adobe aren't really there with the support, but i'm having a real issue finding out where the issue lies.

I have been rolling out desktops, they're all the same copy of a master image.

Running Ubuntu 8.04, Firefox3 with the latest flash/java via Ubuntu-restricted-extras (hopefully this makes sense).

Basically a developer has created a new CRM system for us, using Flex, they access the CRM via an internal address which produces a .swf movie which the user logs into.

80% of people, have no issue. The rest will have a bug where the CRM will hang doing some work, I assume this is a fault in the CRM itself, the only thing they can do is logout, which requests them to then login.

This is where the problems with Firefox start, I think. They press login and thats it, it hangs.

If I close Firefox and retry.. no joy, same thing. The only way I can give it a kick is to clear the cache from Firefox.

I thought it was a proxy issue so made the clients ignore that local address but it still happens.

Kinda a tricky one without really being able to show the CRM! 

Sometimes when they close Firefox the .parentlock file doesn't remove itself, deleting it messes up the profile so I have to re-make it. 

Do ANY of these problems sound... familiar? hehe

Is it a Flash issue? Is it a Firefox Issue?

Ninja edit : 64 bit machine, running 32bit Ubuntu w/ 32bit FF/Flash etc

---

### Post by Execute_Method on 2008-07-10
I have had issues regarding FF3 stable and flash. My problems mainly deal with cpu load and hanging.

[http://ubuntuforums.org/showthread.php?t=854484](http://ubuntuforums.org/showthread.php?t=854484)

You are right about the suck of Adobe not being very supportive, however they may be changing their tune a little. they just released a beta of Flash10 which supports Ubuntu and other linux ditros. I installed it the other day, but haven't had a chance to do too much testing. If you wanna give it a try it is here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by t_k on 2008-07-10
Flash 10 beta with Firefox or Opera works flawlessly. Very low CPU usage too.

---

