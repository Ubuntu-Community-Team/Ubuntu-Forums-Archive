---
title: "small problem with conky loading config"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by thefatmoop on 2008-01-09
I must be missing something extremely obvious here... I installed conky using synaptic package manager, i can't get it to open using a different config when the "conky" command is used. 

so for example
```
conky -c ~/config.conkyrc
```
works and it will load the config i want. 

when i placed the config.conkyrc into /home/username/config.conkyrc it didn't work =/ 

on the sessions i tired the command used above "conky -c ~/config.conkyrc" and it still loaded default 

tried using a script 
```
#!/bin/bash

sleep 5 &&
conky -d -c /home/config.conkyrc &
exit
```

didn't work.. if anyone can help plz ^^ thanks lol i'm sure this is a totally noob question

what does the exact name of the config need to be? and i just make a normal text doc (right clicking desktop>create document>empty file)?

(on ubuntu 7.10)

---

### Post by thefatmoop on 2008-01-09
le bump plz some1

---

### Post by ssteinbr on 2008-01-09
I'm pretty sure that the config file that conky looks for when it runs is simply called ".conkyrc" not "config.conkyrc".  Hope this helps.

---

