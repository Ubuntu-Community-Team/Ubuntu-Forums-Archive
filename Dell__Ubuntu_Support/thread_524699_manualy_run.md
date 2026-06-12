---
title: "manualy run"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by maineman2 on 2007-08-13
How can I manualy run "dpkg --configure -a? It says the down load was interupted Thanks Dan

---

### Post by overdrank on 2007-08-15
> **maineman2 said:**
> How can I manualy run "dpkg --configure -a? It says the down load was interupted Thanks Dan

Hi if you have not solved your issue then you can run that command in the terminal located under applications, accessories, terminal. Run this command 
```
sudo dpkg --configure -a
```
It may ask you to run 
```
sudo apt-get install -f 
```
Also so this will correct your issues. Post back if additional help is needed. :)

---

