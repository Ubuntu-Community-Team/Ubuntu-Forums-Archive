---
title: "crashed x"
date: 2006-09-12
forum: Desktop Environments
---

### Post by black-DraGon on 2006-09-12
hi,
i have a big problem with my x-server. 
Der X-Server (die graphisch Benutzeroberfläche) konnte nicht gestartet werden. Es ist möglicherweise nicht korrekt konfiguriert.
now i cant start visual, just baseline.
i tried to install an thememanager yesterday and after that the answer above came up. what i have to do to came back to my x????
pleas help me
greetz
black-DraGon

---

### Post by ayoli on 2006-09-12
try this in command line:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by black-DraGon on 2006-09-12
thanks i will.
if i try to sudo apt-get update or upgrade than i get an error for compiz...
thats a pacage which comes with tat programm what i tryed to install...

*edit*
now i tried what ayoli sad but it wont work...
the mount check starts now after 30 times and sais taht a dubble used point? i dont know exactly what error but it will start again and every time the same error...
sorry for my bad english.
how can i uninstall software in the baseline? if i came back to the baseline...
i want to uninstall that compiz crap.](*,) ](*,) ](*,)

---

### Post by ayoli on 2006-09-12
what was this program you installed that compiz comes with ?
to remove compiz:
```
apt-get remove compiz compiz-core
```
did you also install xgl or xorg-air ?
btw, i m not sure that the check error on your fs is related to your X problem.

---

### Post by black-DraGon on 2006-09-12
ahm... i dont know exactly but it was cgwd or something like that...
i want to become nice glassy optic on my ubuntu and read that i have to install compiz. so i go to synaptic and search for compiz. after the installation my x was broken...
i am near to cry... i have a second disk, god thank, to go online but my first disk is wrealy wrealy important to me. i have to repair my x.

---

### Post by black-DraGon on 2006-09-12
now i have tried a lot but no solution...
can anyone help me?

---

