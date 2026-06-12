---
title: "Problem with Unity(or launcher?)"
date: 2017-03-21
forum: Desktop Environments
---

### Post by djday01 on 2017-03-21
So lately untiy has been doing some weird stuff on me, I noticed that every time i open up a terminal or run gedit, for some reason, they all minimize to the thunderbird tab?  Was wondering if this is a untiy problem, launcher problem, or a thunderbird problem?  Has anyone else had similar problems?  If so, how do you fix it?

---

### Post by Karolina.K on 2017-03-22
you haven¨t configured it or so? try updating i remember i had some similar problem some year ago, i think i reinstalled it though.

---

### Post by Frogs Hair on 2017-03-24
> **djday01 said:**
> So lately untiy has been doing some weird stuff on me, I noticed that every time i open up a terminal or run gedit, for some reason, they all minimize to the thunderbird tab?  Was wondering if this is a untiy problem, launcher problem, or a thunderbird problem?  Has anyone else had similar problems?  If so, how do you fix it?

You can try the following commands. 
```
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``` To reset Unity if there is no change.```
setsid unity
```

---

