---
title: "Help with transferring packages?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by rockusnarus on 2005-12-15
Most of my friends either have a dialup connection or a download limited net connection. So it is not possible to download the packages. Can anybody suggest any way i could transfer the packages installed in my system?
I mean not by downloading the deb packages but rather transferring the packages I installed with synaptic. Please help[-o<

---

### Post by soulestream on 2005-12-15
ill bite. Why would you not want to download the deb package?

i havent used synaptic, but i believe it will give you a list of dependencies needed. 

Im new to the whole apt-get thing, but im sure the packages that synaptic downloads might be cached somewhere, you might just be able to copy them from there.

soule

---

### Post by curtis on 2005-12-15
Have a look in /var/cache/apt/archives

---

### Post by rockusnarus on 2005-12-16
[quote=curtis]Have a look in /var/cache/apt/archives[/quote]
Actually the oddest thing occured. I checked the folder for the files and they were present there. But after a while they just disappeared!!! Am I seeing things???:confused:

---

### Post by rockusnarus on 2005-12-16
[quote=soulestream]ill bite. Why would you not want to download the deb package?

i havent used synaptic, but i believe it will give you a list of dependencies needed. 

Im new to the whole apt-get thing, but im sure the packages that synaptic downloads might be cached somewhere, you might just be able to copy them from there.

soule[/quote]
Actually I have a very slow conncetion (64kbps) with time limit from 10 pm to 8 am. So you can imagine my situation...:(

---

### Post by Mustard on 2005-12-16
[QUOTE=rockusnarus]Actually the oddest thing occured. I checked the folder for the files and they were present there. But after a while they just disappeared!!! Am I seeing things???:confused:[/QUOTE]

Synaptic has preferences in its settings for clearing the cache of packages when certain conditions occur.  Check your Synaptic Package Manager preferences.

---

