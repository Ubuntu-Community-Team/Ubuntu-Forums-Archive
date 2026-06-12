---
title: "Something diffferent about the terminal"
date: 2008-12-07
forum: General Help
---

### Post by johnnyxxxcakes on 2008-12-07
Wheneever I do a 'sudo apt-get autoremove' I always get a bunch of random spaces and new lines in the terminal, that I never had before.

> 
john@john-laptop ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done









0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 


---

### Post by SmokinJuan on 2008-12-07
Have you tried to select any text that may be in that blank space?  Perhaps its the same color as the background.

---

### Post by johnnyxxxcakes on 2008-12-07
> **SmokinJuan said:**
> Have you tried to select any text that may be in that blank space?  Perhaps its the same color as the background.

Nope, it's just a bunch of blank space. It does the same thing with 'sudo apt-get autoclean' as well.

EDIT: Sometimes it has less line breaks.

For instance:
> 
john@john-laptop ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree... 50%



Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 
john@john-laptop ~ $ 


---

### Post by geirha on 2008-12-07
To me it looks like your enter/return key is sending more than one signal. Have you by any chance spilt anything into the keyboard lately? Ubuntu Cola perhaps? :)

Try running ```
xev
``` in a terminal, then hit the enter key. It should only list one KeyPress event and one KeyRelease event.

---

