---
title: "problem with unity 5.0, ubuntu 11.10"
date: 2012-01-13
forum: Desktop Environments
---

### Post by darukas on 2012-01-13
i have ugraded my uniti to 5.0v by this instructions: [http://www.upubuntu.com/2012/01/how-to-install-unity-50-under-ubuntu.html](http://www.upubuntu.com/2012/01/how-to-install-unity-50-under-ubuntu.html)

situacion what i have, is that my laptop is overheating,before everything was ok.

maybe posible to rstore old unity version,or somehow fix overheating problem. (by my opinion unity works more faster then before :) )

---

### Post by Krytarik on 2012-01-13
To downgrade to the version in the official repos, run:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging
```To fix the overheating issue; no idea. :P

Regards.

---

### Post by BC59 on 2012-01-13
A solution would be installing the Ubuntu-Tweak (older version) and purge the PPA of Unity 5.0.

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update && 
sudo apt-get install ubuntu-tweak-0

```

---

