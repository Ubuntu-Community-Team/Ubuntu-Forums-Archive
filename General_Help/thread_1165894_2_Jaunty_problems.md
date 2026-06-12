---
title: "2 Jaunty problems"
date: 2009-05-21
forum: General Help
---

### Post by The-ITu on 2009-05-21
hey all
(i know these are probably noob problems)
i recently installed Ubuntu Jaunty Jackalope on my home computer but there are now 2 problems.
1. it can connect to the network but firefox or the terminal don't seam to think they are connected.
2. synaptic only shows installed packages. i want it to show all packages, installed or not.

Thank you
The-ITu

---

### Post by bacardiandwatermelon on 2009-05-21
1. Are you getting an ip address? Run this in terminal.
```
ifconfig
```2. Sounds like you need to enable your universe and multiverse repositories..
[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

Whoops the link is for Hardy... But you get the idea..

---

### Post by Aearenda on 2009-05-21
Problem 2 may be a symptom of problem 1, ie Synaptic is only showing you stuff it got from the install CD.

---

### Post by The-ITu on 2009-05-23
> **bacardiandwatermelon said:**
> 1. Are you getting an ip address? Run this in terminal.
```
ifconfig
```2. Sounds like you need to enable your universe and multiverse repositories..
[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

Whoops the link is for Hardy... But you get the idea..
it just returned a lot of writing which i did not recognise any of it.
also the Netgrear wireless receiver usually has a flashing light in windows, but here it just stays on rather than flashes. 
I have no doubt that there is some kind of connection.
any tip from anyone?

---

### Post by Aearenda on 2009-05-23
The idea is that you tell us what ifconfig said, otherwise we can't help :-)

(If you don't want to type it all, do ```
ifconfig >ifconf.txt
```and then copy the ifconf.txt file to where you can open it and paste it in to the web page.)

---

### Post by The-ITu on 2009-05-23
> **Aearenda said:**
> The idea is that you tell us what ifconfig said, otherwise we can't help :-)

(If you don't want to type it all, do ```
ifconfig >ifconf.txt
```and then copy the ifconf.txt file to where you can open it and paste it in to the web page.)
O ok sorry i dident understand :) il do that soon.

---

### Post by ActiveFrost on 2009-05-23
If Firefox & terminal "thinks" that you are not connected to the internet, why Synaptic should ( which means that you have only 1 "problem", not 2 ) ?
Anyway, what type of connection do you have/had ( wireless, wired, cable .. ) ?

---

### Post by The-ITu on 2009-05-23
> **ActiveFrost said:**
> If Firefox & terminal "thinks" that you are not connected to the internet, why Synaptic should ( which means that you have only 1 "problem", not 2 ) ?
Anyway, what type of connection do you have/had ( wireless, wired, cable .. ) ?
wireless.
also the Netgrear wireless receiver usually has a flashing blue light on windows while on Ubuntu it just says on constantly rather than flashing.

---

