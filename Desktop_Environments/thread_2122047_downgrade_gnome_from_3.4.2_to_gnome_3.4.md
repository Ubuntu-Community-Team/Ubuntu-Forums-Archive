---
title: "downgrade gnome from 3.4.2 to gnome 3.4"
date: 2013-03-03
forum: Desktop Environments
---

### Post by crazymonkey05 on 2013-03-03
hello i recently upgraded gnome to 3.5.4 and well i love the look but miss my extensions and add ons so is there a way to downgrade to gnome 3.4 again or do i have to do a clean system install????

---

### Post by Frogs Hair on 2013-03-04
I am guessing you are referring to the gnome shell.  What Ubuntu version and how did you upgrade ? If a PPA was used to install it is possible to remove it an install the current version from the software center. I believe  12.04 uses 3.4.2  and I see on my installation that 12.10 uses 3.6.2 which has compatible extensions.

---

### Post by crazymonkey05 on 2013-03-04
yes it was via ppa and now i am on a developers release and cant figure out how to downgrade or upgrade and i am on ubuntu 12.04

---

### Post by Frogs Hair on 2013-03-04
There is a purge available for the ricotz PPA but it is from last year. 

[http://www.infty.nl/wordpress/2012/09/manual-ppa-purge-for-ricotz-testing-and-staging-ppas/](http://www.infty.nl/wordpress/2012/09/manual-ppa-purge-for-ricotz-testing-and-staging-ppas/)

Another way would be to use the following command/s. ```
sudo apt-get remove --purge gnome-shell 
``` 
Next, open Software Sources > Other Software and remove the correct PPA source. There will be _two_ lines with the same address.
 
Update sources list: ```
sudo apt-get update 
``` 

Install shell from Ubuntu repository: ```
sudo apt-get install gnome-shell
```

---

### Post by crazymonkey05 on 2013-03-07
thank you so much did that now im back om 3.4.1 and got all my extensions again i cant thank you enough .... :):):)

---

### Post by Frogs Hair on 2013-03-08
I'm glad to worked out for you . With the PPA changing constantly extensions may become incompatible due to updates. The [COLOR=#000000]ricotz PPA is advertised as a testing PPA.[/COLOR]

---

