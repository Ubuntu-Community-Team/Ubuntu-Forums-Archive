---
title: "kwin redmond theme sources?"
date: 2011-04-18
forum: Desktop Environments
---

### Post by josvanr on 2011-04-18
Kubuntu 10.10 looking for the sources of kwin redmond theme. I think its just in a sub directory of kwin. But I can't seem to find the sources when I search for kwin in the package installer (nor synaptic). I have selected the source codes in the 'package sources'..

josvanr

---

### Post by Zorael on 2011-04-19
They're in **kdeartwork**.

```
./kdeartwork-4.6.2/kwin-styles/redmond
./kdeartwork-4.6.2/kwin-styles/redmond/redmond.cpp
./kdeartwork-4.6.2/kwin-styles/redmond/redmond.desktop
./kdeartwork-4.6.2/kwin-styles/redmond/redmond.h
```

---

### Post by josvanr on 2011-04-23
gracias mucas..

---

### Post by josvanr on 2011-04-23
hmm I can find the package, but not the sources, though i did 
check 'sources' in the 'edit origins' dialog.... When I search
for 'kdeartwork' in packageedit, no sources turn up..

josvanr

---

### Post by josvanr on 2011-04-23
case anyone doesn't know yet: the sources aren't shown in
'packageedit' for some reason. One has to do

sudo apt-get source kdeartworks

(or whatever source package you want)



!"@*&#

---

