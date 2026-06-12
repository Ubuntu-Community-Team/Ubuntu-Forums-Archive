---
title: "Problems using www.map24.com"
date: 2006-07-25
forum: Desktop Environments
---

### Post by tgrzejsz on 2006-07-25
Hi,
I have problems using map24 ([www.map24.com](www.map24.com)) map service with all of the following browsers:
-konqueror: shows error message about too deep call stack in javascript.
-firefox: nearly works, but infinitely scales the map window every second. The page gets refreshed and the site is virtually unusable, although I can see the map that I want to see.
-opera 9.0: presents a map window that is much smaller then it should be and that lacks some functionality (the map controls on the bottom of the map window). Also every drag of the map causes the browser window to refresh which makes browsing a map very slow.

Did somebody somehow managed to make it work?

Thanks,
Tomek

---

### Post by llamakc on 2006-07-25
I just used it successfully. Firefox 1.5.0.4

---

### Post by Tamihania on 2006-07-25
I have absolutely no problem in using the webpage - BTW - I've just checked the way from Oslo to Warszawa. Do you have java plugin installed for your browsers? It needs it.

Kind regards from Oslo,

Pozdrowienia,

tami

---

### Post by tgrzejsz on 2006-07-27
Hi,
Thanks for the answers. Of course I have the java plugin installed, otherwise I wouldn't see a thing. The problem is, as I've already wrote, that in Firefox the map window constantly scales verticaly, bit by bit, refreshing webpage everytime. This is kind of unusual and unsuspected behaviour. Unfortunately it looks, like it is not common, so I can't get much help.

Greetings,
Tomek

---

### Post by tgrzejsz on 2006-08-04
Hello again,
So after some investigation it looks like problem is connected with using Adblock. After disabling adblock I can happily use map24 with firefox.

Greetings,
Tomek

---

### Post by ^rooker on 2007-05-08
I've also had problems with Firefox and map24.com - Here's how I've managed to get it work (in case someone else needs it):

**[Problem]**
- No java plugin installed, so I got a static map.
- Installed "j2re1.4-mozilla-plugin", which caused even more problems because it FF froze when map24 was trying to load the map.


**[Solution]**
I've now installed "sun-java5-plugin" and everything works like a charm now.

---

